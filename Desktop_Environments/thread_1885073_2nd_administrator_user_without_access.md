---
title: "2nd administrator user without access?"
date: 2011-11-22
forum: Desktop Environments
---

### Post by cajunlibra on 2011-11-22
I have Ubuntu 11.10 installed with all updates.
I created a 2nd user that I designated as an administrator yet it seems to have very few privileges.
For instance, it cannot save files in its own folders in its own home folder such as Documents, Downloads, Desktop, etc. 
It cannot run Chromium, or the Software Center.

I have double-checked and made sure that it is an administrator. I have even gone so far as opening nautilus as root and the making everything int he home folder with privileges for this user. That didn't work.

What else can i do?  I did restore files from a previous version using SBackup for this profile.  How do i fix this?


Thanks

---

### Post by cajunlibra on 2011-11-29
Anyone? 

I didn't have this problem before I upgraded to 11.10.

---

### Post by fdrake on 2011-11-29
> **cajunlibra said:**
> 
I created a 2nd user that I designated as an administrator yet it seems to have very few privileges.
For instance, it cannot save files in its own folders in its own home folder such as Documents, Downloads, Desktop, etc. 
It cannot run Chromium, or the Software Center.
how did u create this user?

---

### Post by cajunlibra on 2011-11-29
System Settings > User accounts > +

This worked fine in 10.10 and 11.04

---

### Post by fdrake on 2011-11-29
Can you post the output of
```

ls -al /home/admin_user/

```
where in "admin_user" you put the name of the user.

---

### Post by cajunlibra on 2011-11-29
```
total 268
drwxrwxr-x 32 practice practice  4096 2011-11-29 20:24 .
drwxr-xr-x  5 root     root      4096 2011-11-05 14:10 ..
drwxrwxr-x  3 practice practice  4096 2011-11-05 15:08 .adobe
-rw-------  1 practice practice    73 2011-11-22 10:48 .bash_history
-rw-r--r--  1 practice practice   220 2011-11-05 14:10 .bash_logout
-rw-r--r--  1 practice practice  3353 2011-11-05 14:10 .bashrc
drwxrwxr-x 16 practice practice  4096 2011-11-22 12:33 .cache
drwx------  3 practice practice  4096 2011-11-29 20:23 .compiz
drwxrwxr-x  3 practice practice  4096 2011-11-08 10:39 .compiz-1
drwxrwxr-x 10 root     root      4096 2011-10-15 17:12 .config
drwxrwxr-x  3 practice practice  4096 2011-11-05 15:05 .dbus
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Desktop
-rw-rw-r--  1 practice practice    26 2011-11-29 19:29 .dmrc
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Documents
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Downloads
-rw-------  1 practice practice    16 2011-11-05 15:05 .esd_auth
-rw-r--r--  1 practice practice   179 2011-11-05 14:10 examples.desktop
drwxrwxr-x  2 root     root      4096 2011-10-08 13:31 .fontconfig
drwxrwxr-x  4 practice practice  4096 2011-11-29 19:29 .gconf
drwxrwxr-x  5 practice practice  4096 2011-11-08 11:14 .gnome2
drwxrwxr-x  2 practice practice  4096 2011-11-05 15:06 .gnome2_private
-rw-------  1 practice practice     0 2011-11-26 16:13 .goutputstream-51ZO5V
-rw-------  1 practice practice     0 2011-11-26 14:57 .goutputstream-ARWL5V
-rw-------  1 practice practice     0 2011-11-26 15:11 .goutputstream-UMWX5V
-rw-------  1 practice practice     0 2011-11-22 10:57 .goutputstream-XWHW4V
drwxrwxr-x  2 root     root      4096 2011-10-08 12:59 .gstreamer-0.10
-rw-r--r--  1 root     root       137 2011-10-17 21:42 .gtk-bookmarks
drwxr-xr-x  2 practice practice  4096 2011-11-05 15:05 .gvfs
drwxrwxr-x  2 practice practice  4096 2011-11-29 20:23 .hplip
-rw-------  1 practice practice  7014 2011-11-29 19:29 .ICEauthority
drwxrwxr-x  3 practice practice  4096 2011-11-08 11:02 .libreoffice
drwxrwxr-x  3 root     root      4096 2011-08-09 22:50 .local
drwxrwxr-x  3 practice practice  4096 2011-11-05 15:08 .macromedia
drwxrwxr-x  3 practice practice  4096 2011-11-05 15:05 .mission-control
drwxrwxr-x  4 practice practice  4096 2011-11-05 15:06 .mozilla
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Music
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Pictures
drwxrwxr-x  3 practice practice  4096 2011-11-08 11:27 .pki
-rw-r--r--  1 root     root       675 2010-04-18 20:51 .profile
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Public
drwx------  2 practice practice  4096 2011-11-29 19:29 .pulse
-rw-------  1 practice practice   256 2011-11-05 15:05 .pulse-cookie
drwx------  5 practice practice  4096 2011-11-29 19:46 .Skype
-rw-r--r--  1 root     root         0 2011-08-09 22:52 .sudo_as_admin_successful
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Templates
drwxrwxr-x  4 practice practice  4096 2011-11-22 12:58 .thumbnails
drwxrwxr-x  2 root     root      4096 2011-08-09 22:49 Videos
-rw-------  1 practice practice     0 2011-11-29 20:24 .Xauthority
-rw-------  1 practice practice 92423 2011-11-29 20:24 .xsession-errors
```

---

