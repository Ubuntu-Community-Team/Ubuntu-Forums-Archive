---
title: "File and folder permissions"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Rondonjin on 2006-06-05
In another thread on updating Firefox I found out that some of the permissions on the files and folders in my /home partition were not right. This is prolly the result of going through three different distros and different versions and switching from KDE to Gnome in the process. My question is, what should they be, are the hidden ones different from the visible folders? What about my files?

Any help appreciated.

Wayne

---

### Post by aysiu on 2006-06-05
I don't if this helps, but: ```
ls -al
drwxr-xr-x 29 username username   4096 2006-06-04 23:02 .
drwxr-xr-x  3 root root   4096 2006-05-31 22:50 ..
-rw-------  1 username username   5142 2006-06-04 22:13 .bash_history
-rw-r--r--  1 username username    220 2006-05-31 22:50 .bash_logout
-rw-r--r--  1 username username    414 2006-05-31 22:50 .bash_profile
-rw-r--r--  1 username username   2227 2006-05-31 22:50 .bashrc
drwx------  4 username username   4096 2006-06-01 23:44 .cache
drwxr-xr-x  6 username username   4096 2006-06-01 23:44 .config
drwxr-xr-x  2 username username   4096 2006-06-04 23:01 Desktop
-rw-------  1 username username     24 2006-06-01 23:45 .dmrc
-rw-------  1 username username     16 2006-06-01 05:57 .esd_auth
-rw-r--r--  1 username username 105901 2006-06-01 06:20 .fonts.cache-1
-rw-r--r--  1 username username    514 2006-06-03 00:27 .fonts.conf
drwxr-xr-x  6 username username   4096 2006-06-02 09:51 .fullcircle
drwx------  4 username username   4096 2006-06-04 23:02 .gconf
drwx------  2 username username   4096 2006-06-04 23:03 .gconfd
drwxr-xr-x 21 username username   4096 2006-06-04 20:26 .gimp-2.2
-rw-r-----  1 username username      0 2006-06-04 20:19 .gksu.lock
drwxr-xr-x  3 username username   4096 2006-06-01 05:57 .gnome
drwx------ 16 username username   4096 2006-06-04 22:55 .gnome2
drwx------  2 username username   4096 2006-06-01 05:57 .gnome2_private
drwx------  2 username username   4096 2006-06-01 09:25 .gnupg
drwxr-xr-x  2 username username   4096 2006-05-31 23:22 .gstreamer-0.10
-rw-------  1 username username    133 2006-06-01 21:03 .gtk-bookmarks
-rw-r--r--  1 username username     86 2006-06-04 22:40 .gtkrc-1.2-gnome2
-rw-------  1 username username    801 2006-06-04 23:02 .ICEauthority
drwxr-xr-x  4 username username   4096 2006-06-02 20:24 .icons
drwx------  4 username username   4096 2006-06-01 23:43 .kde
-rw-------  1 username username    307 2006-06-03 00:27 .kderc
-rw-------  1 username username     35 2006-06-04 22:13 .lesshst
drwxr-xr-x  3 username username   4096 2006-06-03 16:08 .local
drwx------  3 username username   4096 2006-06-01 22:31 .macromedia
drwxr-xr-x  3 username username   4096 2006-06-01 21:58 .mcop
-rw-------  1 username username     31 2006-06-03 15:47 .mcoprc
drwx------  3 username username   4096 2006-06-01 05:57 .metacity
lrwxrwxrwx  1 username username     37 2006-06-04 18:39 .mozilla -> /documents/linux_acc essories/.mozilla
lrwxrwxrwx  1 username username     41 2006-06-01 05:59 .mozilla-thunderbird -> /documen ts/linux_accessories/.thunderbird
drwxr-xr-x  3 username username   4096 2006-06-01 05:57 .nautilus
drwxr-xr-x  2 username username   4096 2006-06-04 22:56 .qt
-rw-------  1 username username  40064 2006-06-04 21:36 .recently-used
-rw-r--r--  1 username username      0 2006-06-01 05:57 .sudo_as_admin_successful
drwxr-xr-x  4 username username   4096 2006-06-04 22:34 .themes
drwx------  5 username username   4096 2006-06-04 22:58 .thumbnails
lrwxrwxrwx  1 username username     41 2006-05-31 23:31 .thunderbird -> /documents/linux _accessories/.thunderbird
drwx------  2 username username   4096 2006-06-04 22:19 .Trash
drwx------  2 username username   4096 2006-06-01 05:57 .update-notifier
drwxr-xr-x  2 username username   4096 2006-06-04 21:25 .wapi
-rw-------  1 username username    117 2006-06-04 23:02 .Xauthority
-rw-------  1 username username    192 2006-06-03 00:28 .xcompmgrrc
drwxr-xr-x  2 username username   4096 2006-06-01 09:37 .xine
-rw-r--r--  1 username username  11414 2006-06-03 00:39 .xscreensaver
-rw-r--r--  1 username username    416 2006-06-04 23:02 .xsession-errors
```

---

### Post by Rondonjin on 2006-06-05
[QUOTE=aysiu]I don't if this helps, but: ```
ls -al
drwx------  2 username username   4096 2006-06-01 05:57 .update-notifier
drwxr-xr-x  2 username username   4096 2006-06-04 21:25 .wapi
-rw-------  1 username username    117 2006-06-04 23:02 .Xauthority
-rw-------  1 username username    192 2006-06-03 00:28 .xcompmgrrc
drwxr-xr-x  2 username username   4096 2006-06-01 09:37 .xine
-rw-r--r--  1 username username  11414 2006-06-03 00:39 .xscreensaver
-rw-r--r--  1 username username    416 2006-06-04 23:02 .xsession-errors
```[/QUOTE]


Thanks, I seem to have mostly drwxrwxr-x, especially on folders. Need a few cold ones and some time to sort things out.

Wayne

---

