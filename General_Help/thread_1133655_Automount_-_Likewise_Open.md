---
title: "Automount - Likewise Open"
date: 2009-04-23
forum: General Help
---

### Post by pinguino99 on 2009-04-23
I succesfully used likewise open 5  for authenticating against a windows 2003 active directory domain.
I can login with my AD user/password.

But i am not able to modify the pam_mount xml file for automounting samba shares of the windows file server.

Please, anyone giving me instructions for do that ?
I am on jaunty....

Regards, and thanks to all.

---

### Post by wink311 on 2009-04-28
bump

---

### Post by pinguino99 on 2009-05-05
bump

---

### Post by wink311 on 2009-05-08
super bump.

---

### Post by pinguino99 on 2009-05-13
triple bump !

This explains that, in business, linux desktops are not so used...

---

### Post by Bufke on 2010-05-13
Well in case someone is searching it is actually possible after working through a few bugs.

[http://davidmburke.com/2010/03/30/linux-and-active-directory/](http://davidmburke.com/2010/03/30/linux-and-active-directory/)

---

### Post by HelpyHelperton on 2010-06-24
Here's a configuration I know works on Ubuntu 10.04, my Domain Controller is Windows 2003

/etc/security/pam_mount.conf.xml

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
        See pam_mount.conf(5) for a description.
-->

<pam_mount>


                <!-- Volume definitions -->


                <!-- pam_mount parameters: General tunables -->

<debug enable="1" />
<!-- <luserconf name=".pam_mount.conf.xml" /> -->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<logout wait="0" hup="0" term="0" kill="0" />


                <!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="true" />

<volume user="*" mountpoint="/home/%(USER)" path="homes/%(USER)" server="lwdemodc01" fstype="cifs" options="nodev,nosuid,uid=%(USERUID),gid=%(USERGID),file_mode=0600,dir_mode=0700,sec=krb5i" />

</pam_mount>
~


/etc/pam.d/common-auth

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=3 default=ignore]      pam_unix.so nullok_secure 
# here's the fallback if no module succeeds
auth    required        /lib/security/pam_lsass.so try_first_pass
auth    sufficient      pam_mount.so
auth    requisite       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required        pam_permit.so
# and here are more per-package modules (the "Additional" block)
#auth   optional        pam_mount.so 
# end of pam-auth-update config

/etc/pam.d/common-account

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.
#

# here are the per-package modules (the "Primary" block)
account [success=3 new_authtok_reqd=done default=ignore]        pam_unix.so debug
# here's the fallback if no module succeeds
account required                        /lib/security/pam_lsass.so                      unknown_ok
account sufficient                      /lib/security/pam_lsass.so
account requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

---

### Post by Ganapathy Santhanam on 2010-10-05
Hi All,

I got a CIFS share from Netapp filer, i got all the configuration as you people has. but still i dont see any mount process happening, is there a way to troubleshoot with the syslogs?

Regards,
Ganapathy Santhanam

---

### Post by atworkwithjf on 2010-10-12
[pinguino99]("http://ubuntuforums.org/member.php?u=325178"),

I'm not sure if you have seen this but:

[http://www.likewise.com/community/index.php/forums/viewthread/825/](http://www.likewise.com/community/index.php/forums/viewthread/825/)

---

