---
title: "SLIM login manager + change ldap passwd problem"
date: 2009-11-04
forum: Desktop Environments
---

### Post by jagnikam on 2009-11-04
Hi All,

System Info 

OS : ubuntu 9.04
login manager : slim
Desktop Environment : lxde 
Auth Type : ldap 

I have created above system before 10 days. 
I have set passwd expiry in ldap server for all users after 15 days there password will expire . users can change there passwd from command prompt but slim login manager does not show any passwd change option.

1) I wanted to know weather slim login manager support to change passwd option for ldap.
2) if yes then where am i going wrong... config files are as follows 


Config file setting 

/etc/pam.d/common-account

account sufficient pam_ldap.so
account required pam_unix.so

 
/etc/pam.d/common-auth

auth sufficient pam_ldap.so
auth required pam_unix.so nullok_secure use_first_pass

 

/etc/pam.d/common-password

password sufficient pam_ldap.so
password required pam_unix.so nullok obscure min=4 max=8 md5

---

