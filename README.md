Ansible Role - Configure SSH
=========

Applies baseline sshd configuration for enterprise linux hosts.

- Will eventually be compliant with CIS SSH benchmarks for popular platforms
- Dynamically define configuration parameteres as well as the banner.

the banner (issue.j2) contains a header, body, and footer used for structuring and easily updating various components such as including logos, contact info, etc.

Configurations are currently intrapolated and are not validated. Ensure correct configuration parameters are passed to the role in order to prevent accidental lockouts!

Requirements
------------

For testing, molecule, vagrant, and libvirt provider is required.

Role Variables
--------------

```
configure_sshd_banner_header: |
  *******************************************************************************
           UNAUTHORIZED ACCESS IS PROHIBITED! CLOSE YOUR CONNECTION NOW!                     
  *******************************************************************************

configure_sshd_banner_body: |
  {{ configure_sshd_organization_name }} - All Rights Reserved
  
  This computer system is under the ownership of The Pharm, LLC. Which contains
  confidential corporate information. Unauthorized Access to this computer 
  system(s) or the data contained herein or in transit to/from this system is 
  prohibited! All interactions with this computer are monitored, recorded, and 
  subject to audit. Unauthorized access to this computer is subject to 
  disciplinary action, civil or criminal charges. Evidence may be provided to
  law enforcement.

configure_sshd_banner_footer: |
  By continuing, you consent to these terms.

configure_sshd_organization_name: "silentsysadmin.com"

# In the future, sshd_config options will be specified below
```

Dependencies
------------

No third party role dependencies are used at this time. 

Example Playbook
----------------

```
roles:
  - role: silent-sysadmin.configure_sshd
    vars:
      configure_sshd_organizaiton_name: "generic ltd"

```

License
-------

MIT

Author Information
------------------

silentsysadmin.com