---
title: "[SOLVED] Messed up local authentication trying to set up LDAP"
date: 2008-06-21
forum: Desktop Environments
---

### Post by johnnybeem on 2008-06-21
Hi,
I am trying to set up LDAP on my home network but never have before and frankly don't know what I'm doing. I followed the tutorial below...

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

...after setting up the server with a similar tutorial. I tried setting up my laptop as an LDAP client and failed horribly. The thing hangs for 5-10 minutes on startup then eventually runs like it did before. I tried reversing the client config by removing packages (libpam-ldap libnss-ldap nss-updatedb libnss-db), setting nsswitch.conf back to 

passwd:         compat
group:          compat

Now it is giving me an "Authentication Failed" message at the login window right when I click my name (can't even try entering a password).

I need to get a book for LDAP because I am blindly entering commands from the tutorial and obviously didn't do something right.

For now, can somebody PLEASE help me get this back to the way it was before? I don't want LDAP, I just want local authentication.

---

### Post by johnnybeem on 2008-06-21
Amateur mistake... forgot to reset the lines in /etc/pam.d/(3 files)

all set now

---

### Post by tproberts on 2009-04-01
Hello,

Do you mind sharing the 3 lines that needed reset? I did the exact same thing as you, removing libnss-ldap package and locking myself out of the computer with no chance to enter a password - only username and then the Authentication Failed message.

By the way, 4 of my files in /etc/pam.d/ show recent modification dates: common-account, common-auth, common-password, and common-session. Their contents are:
[common-account]
account  sufficient  pam_ldap.so
account  required  pam_unix.so

[common-auth]
auth  sufficient  pam_ldap.so
auth  required  pam_unis.so nullok_secure use_first_pass

[common-password]
password  sufficient  pam_ldap.so
password  required  pam_unix.so nullok obscure min=4 max=8 md5

[common-session]
session  required  pam_unix.so
session  required  pam_mkhomedir.so skel=/etc/skel/
session  optional  pam_ldap.so
session  optional  pam_foreground.so

What is puzzling is I found many references to comment out the line:
@include common-pamkeyring

but it isn't in my pam.d/gdm file. Further, pam_ldap.so does not return when I try to locate pam_ldap


Thanks,
Tom

---

