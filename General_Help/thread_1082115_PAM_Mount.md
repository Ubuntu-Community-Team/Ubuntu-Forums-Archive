---
title: "PAM_Mount"
date: 2009-02-27
forum: General Help
---

### Post by johnson8707 on 2009-02-27
I might be using the wrong program here but I have installed libpam-mount on my machine. I am trying to get it to mount an SMB share at login and unmount at logoff.

Can someone explain to me how to configure PAM to do this or point me to a detailed HOW TO for it? I've never used PAM before so I'm new to it.


Thanks!

---

### Post by albandy on 2009-02-27
edit /etc/pam.d/gdm

search for the line @include common-session
and add this new one: @include common-pammount

your file should look like this:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-pammount
@include common-password



now you should configure /etc/security/pam_mount.conf.xml

---

### Post by johnson8707 on 2009-02-27
Alright, so I've made that change. Now I'm in the pam_mount.conf.xml and I go down to where it allows me to edit for SMB mounts.

I put in my servername the volume name and the mount point. I left the username, password, uid, gid, etc fields as they were because I want the users login credentials to be what the machine mounts with.

Am I doing this right? Is there anything else in the pam_mount.conf.xml file I need to edit besdies that one line??

Thanks!

---

### Post by albandy on 2009-03-02
Your mounts should look like this:

<volume fstype="smbfs" server="smbserver.mydomain.es" path="mysharedfolder" mountpoint="/media/%(USER)/m" options="dmask=0700" />

---

### Post by johnson8707 on 2009-03-04
Where would I put that type of command? In the pam_mount.conf.xml file??

Also would that create a mount point and mount the windows share when they log into the linux client?

THANKS!

---

### Post by albandy on 2009-03-04
yes, put it in pam_mount.conf.xml file
then when a user logs in the system automatically pam_mount use the user name and password to mount the shared volume

you will need to have installed the package smbfs to mount smbfs volumes

---

