Ansible Role: Grant AD Group Login
=========

Grant AD group login right on a system configured to connect directly to AD using SSSD.

Requirements
------------

The system is configured to connect directly to AD using SSSD.

For the SSSD configuration, see [Connecting RHEL systems directly to AD using SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/integrating_rhel_systems_directly_with_windows_active_directory/connecting-rhel-systems-directly-to-ad-using-sssd_integrating-rhel-systems-directly-with-active-directory).

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
ad_group_names:
  - "My AD Admins (G)"
  - "My Security Admins"
```

Set these variables in host_vars/hostname.yml to overwrite the default value.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: servers

  tasks:
    - name: config ad group login
      include_role:
        name: sfitpro.ad_group_login
        apply:
          tags:
            - login
      vars:
        ad_group_name: "{{ item }}"
      loop: "{{ ad_group_names }}"
      tags:
        - login
```

License
-------

BSD

Author Information
------------------

This role was created by Eddie Lu.
