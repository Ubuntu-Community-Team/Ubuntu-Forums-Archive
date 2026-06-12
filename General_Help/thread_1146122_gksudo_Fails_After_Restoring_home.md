---
title: "gksudo Fails After Restoring /home"
date: 2009-05-02
forum: General Help
---

### Post by Penguin Guy on 2009-05-02
I backed up home to a tarball on a USB drive using:
[COLOR=Green]sudo tar cvPjf /media/USB-Drive/home.bz2 --exclude=.gvfs /home[COLOR=Black]
and then installed Jaunty and extracted the tarball using:
[COLOR=Green]sudo tar xvpPjf /media/USB-Drive/home.bz2[COLOR=Black]
but now many of my settings are lost (evolution, panel settings, etc) and gksudo doesn't work (meaning I can't use any administrative tools).

* The commands above are from memory so [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Green][COLOR=Black][COLOR=Green][COLOR=Black]may not be the exact commands I typed in.
* During the whole process /home was in it's own partition.

[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Green][COLOR=Black][COLOR=Green][COLOR=Black]What could have gone wrong?

I rebooted and now it has fixed itself.
[/COLOR][/COLOR]
[/COLOR][/COLOR]

---

### Post by taurus on 2009-05-02
Have you looked at the ownership and permissions of your $HOME?  Make sure you are the ownership of those files and directories and the permissions are what they should be.

```
ls -la ~
```

---

### Post by Penguin Guy on 2009-05-02
It looks wrong to me (shouldn't they all be [COLOR=Green]rw-r--r--[COLOR=Black])[/COLOR][/COLOR] but I'll wait for a reply before doing anything stupid:
```
~$ ls -la ~
total 576
drwxr-x--- 66 josh josh   4096 2009-05-02 15:36 .
drwxr-xr-x  6 root root   4096 2009-04-29 18:07 ..
drwx------  3 josh josh   4096 2009-02-09 16:48 .adobe
drwxr-xr-x  2 josh josh   4096 2009-03-05 21:19 .audacity1.3-josh
drwxr-xr-x  4 josh josh   4096 2009-03-05 21:19 .audacity-data
drwxr-xr-x  3 josh josh   4096 2009-03-15 14:36 .avidemux
drwxr-xr-x  5 josh josh   4096 2009-05-02 14:50 Backgrounds
-rw-------  1 josh josh   8647 2009-05-02 15:10 .bash_history
-rw-r-----  1 josh josh    220 2009-02-07 16:23 .bash_logout
-rw-r-----  1 josh josh   3306 2009-04-21 18:08 .bashrc
-rw-r-----  1 josh josh   3179 2009-04-16 12:23 .bashrc~
lrwxrwxrwx  1 josh josh     15 2009-05-02 13:04 bin -> /home/share/bin
drwx------  2 josh josh   4096 2009-02-13 16:05 .bogofilter
drwxr-xr-x  7 josh josh   4096 2009-03-10 16:32 .cache
-rw-r--r--  1 josh josh     30 2009-04-20 08:13 Code~
drwx------  3 josh josh   4096 2009-02-08 13:49 .compiz
drwxr-x--- 16 josh josh   4096 2009-04-26 18:16 .config
-rw-r--r--  1 josh josh   4166 2009-04-28 18:35 .conkyrc
-rw-r--r--  1 josh josh   4166 2009-04-28 17:46 .conkyrc~
-rwxrwxrwx  1 josh josh    131 2009-04-19 17:34 Crispin's Code
-rw-rw-rw-  1 josh josh     71 2008-12-18 18:41 Crispin's Code~
drwxr-x---  3 josh josh   4096 2009-02-08 12:35 .dbus
drwxr-xr-x  5 josh josh   4096 2009-03-13 16:14 .designer
drwxr-x---  2 josh josh   4096 2009-05-02 15:36 Desktop
drwxr-xr-x  2 josh josh   4096 2009-04-02 17:14 .devilspie
-rw-------  1 josh josh     28 2009-04-30 15:58 .dmrc
drwxr-x---  2 josh josh   4096 2009-05-02 13:14 Documents
drwxr-x---  2 josh josh   4096 2009-03-02 20:02 .easytag
-rw-r--r--  1 josh josh    670 2009-04-29 19:41 .Easy_Terminal
-rw-r--r--  1 josh josh      0 2009-04-29 19:34 Easy_Terminal~
-rw-------  1 josh josh     16 2009-02-08 12:35 .esd_auth
drwxr-xr-x  8 josh josh   4096 2009-05-02 15:05 .evolution
-rw-r-----  1 josh josh   1195 2009-03-10 16:41 .fbrc
drwxr-xr-x  2 josh josh   4096 2009-05-02 13:12 .fontconfig
drwxr-x---  5 josh josh   4096 2009-05-02 13:40 .gconf
drwxr-x---  2 josh josh   4096 2009-05-02 15:36 .gconfd
drwx------  4 josh josh   4096 2009-02-15 19:29 .gegl-0.0
drwxr-xr-x 22 josh josh   4096 2009-04-23 20:47 .gimp-2.6
-rw-r-----  1 josh josh      0 2009-05-02 15:15 .gksu.lock
drwxr-x--- 19 josh josh   4096 2009-04-30 16:01 .gnome2
drwx------  2 josh josh   4096 2009-02-08 12:35 .gnome2_private
drwxr-x---  2 josh josh   4096 2009-04-30 07:51 .gnupg
drwx------  2 josh josh   4096 2009-03-02 20:21 .gnusound
drwxr-xr-x  2 josh josh   4096 2009-03-13 15:57 .gpilotd
-rw-r-----  1 josh josh      4 2009-03-13 15:57 .gpilotd.pid
drwxr-xr-x  2 josh josh   4096 2009-05-02 14:13 .gstreamer-0.10
-rw-r--r--  1 josh josh    102 2009-05-02 13:02 .gtk-bookmarks
-rw-r-----  1 josh josh    939 2009-04-14 14:56 .gtk-recordmydesktop
dr-x------  2 josh josh      0 2009-05-02 12:06 .gvfs
drwxr-----  2 josh josh   4096 2009-03-07 16:43 .hplip
-rw-------  1 josh josh  18373 2009-04-30 15:58 .ICEauthority
drwxr-xr-x  5 josh josh   4096 2009-04-13 15:29 .icons
drwxr-xr-x  4 josh josh   4096 2009-02-10 20:12 .jagex_cache_32
-rw-r--r--  1 josh josh     34 2009-04-28 16:29 jagex_runescape_preferences.dat
drwxr-xr-x  3 josh josh   4096 2009-02-09 18:34 .java
drwx------  3 josh josh   4096 2009-03-26 17:23 .kde
-rw-------  1 josh josh     35 2009-04-29 16:29 .lesshst
drwx------  3 josh josh   4096 2009-02-08 12:35 .local
-rw-r--r--  1 josh josh    866 2009-04-16 19:05 Lolscript~
-rw-r--r--  1 josh josh    866 2009-04-16 19:07 Lolscript.off
drwx------  3 josh josh   4096 2009-02-09 16:48 .macromedia
drwxr-xr-x  3 josh josh   4096 2009-03-26 17:54 .mcop
-rw-------  1 josh josh     31 2009-03-26 17:54 .mcoprc
drwx------  4 josh josh   4096 2009-03-28 11:38 .mozilla
drwx------  3 josh josh   4096 2009-03-28 11:38 .mozilla-thunderbird
-rw-r-----  1 josh josh      6 2009-04-04 13:29 .musePrj
drwxr-x---  2 josh josh   4096 2009-04-23 19:35 Music
drwxr-xr-x  3 josh josh   4096 2009-03-13 20:04 My Music
drwxr-xr-x  3 josh josh  20480 2009-04-30 08:06 .nautilus
drwx------  3 josh josh   4096 2009-04-27 17:47 .openoffice.org2
lrwxrwxrwx  1 josh josh     29 2009-05-02 13:04 Optical Illusions -> /home/share/Optical Illusions
drwxr-x---  3 josh josh   4096 2009-04-23 17:20 Pictures
-rw-r--r--  1 josh josh     37 2009-05-02 13:16 .printer-groups.xml
-rw-r-----  1 josh josh    800 2009-04-07 12:27 .profile
-rw-r-----  1 josh josh    675 2009-02-07 16:23 .profile~
drwxr-xr-x  2 josh josh   4096 2009-02-09 17:20 Program Files
drwxr-xr-x  4 josh josh   4096 2009-03-27 17:04 Programming
drwxr-x---  2 josh josh   4096 2009-02-08 12:35 .pulse
-rw-------  1 josh josh    256 2009-02-08 12:35 .pulse-cookie
drwx------  6 josh josh   4096 2009-04-30 16:08 .purple
drwxr-xr-x  2 josh josh   4096 2009-03-13 16:06 .qdevelop
drwxr-xr-x  2 josh josh   4096 2009-03-26 17:23 .qt
-rw-------  1 josh josh   4664 2009-04-23 17:08 .recently-used
-rw-------  1 josh josh 125851 2009-05-02 15:36 .recently-used.xbel
drwxrwx---  3 josh josh   4096 2009-03-31 17:13 .sane
-rw-r--r--  1 josh josh    137 2009-04-29 19:56 Scripts
-rw-r--r--  1 josh josh    168 2009-04-29 19:41 Scripts~
drwxr-xr-x  2 josh josh   4096 2009-05-02 13:15 Secure
drwxr-xr-x  2 josh josh   4096 2009-03-02 20:21 .sooperlooper
drwx------  2 josh josh   4096 2009-03-03 19:20 .ssh
-rw-r--r--  1 josh josh      0 2009-02-08 12:41 .sudo_as_admin_successful
drwx------  2 josh josh   4096 2009-05-02 14:33 .synaptic
drwxr-xr-x  9 josh josh   4096 2009-04-13 15:36 .themes
drwxr-xr-x  2 josh josh   4096 2009-04-23 20:22 The Rofl Folder
drwx------  5 josh josh   4096 2009-02-15 19:29 .thumbnails
drwxr-xr-x  2 josh josh   4096 2009-02-08 12:41 .update-manager-core
drwx------  2 josh josh   4096 2009-02-13 17:52 .update-notifier
-rw-r--r--  1 root root    343 2009-04-14 15:00 .usb-creator.log
drwxr-x---  2 josh josh   4096 2009-05-02 14:16 Videos
-rw-------  1 josh josh    735 2009-04-20 18:12 .viminfo
drwxr-xr-x  2 josh josh   4096 2009-03-08 13:06 .VirtualBox
drwxr-xr-x  2 josh josh   4096 2009-04-14 16:23 .wapi
drwxr-xr-x  2 josh josh   4096 2009-03-26 16:25 .winff
-rw-------  1 josh josh    116 2009-04-30 15:58 .Xauthority
drwxr-xr-x  2 josh josh   4096 2009-03-26 17:29 .xine
-rw-r--r--  1 josh josh   3063 2009-04-30 16:01 .xsession-errors
```
And thanks for the reply!

---

### Post by taurus on 2009-05-02
Look in ~/.evolution, ~/.gnome2, & ~/..gnome2_private to make sure the permissions/ownership are still correct.

```
ls -la ~/.evolution
ls -la ~/.gnome2
ls -la ~/.gnome2_private
```
Also, do you belong to group admin?

```
id
```

---

### Post by Penguin Guy on 2009-05-02
```
~$ id
uid=1000(josh) gid=1000(josh) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(josh)
``````
~$ ls -la ~/.evolution
total 136
drwxr-xr-x  8 josh josh  4096 2009-05-02 15:05 .
drwxr-x--- 66 josh josh  4096 2009-05-02 15:36 ..
drwxr-xr-x  4 josh josh  4096 2009-03-13 15:57 addressbook
drwxr-xr-x  3 josh josh  4096 2009-02-13 16:01 cache
drwxr-xr-x  4 josh josh  4096 2009-02-13 16:01 calendar
-rw-r--r--  1 josh josh  3152 2009-02-13 16:01 categories.xml
-rw-------  1 josh josh 65536 2009-05-02 15:05 cert8.db
-rw-------  1 josh josh 16384 2009-05-02 15:05 key3.db
drwxr-xr-x  7 josh josh  4096 2009-05-02 15:05 mail
drwxr-xr-x  4 josh josh  4096 2009-02-13 16:01 memos
-rw-------  1 josh josh 16384 2009-02-13 16:01 secmod.db
drwxr-xr-x  4 josh josh  4096 2009-02-13 16:01 tasks
``````
~$ ls -la ~/.gnome2
total 136
drwxr-x--- 19 josh josh 4096 2009-04-30 16:01 .
drwxr-x--- 66 josh josh 4096 2009-05-02 15:36 ..
drwxr-x---  2 josh josh 4096 2009-05-02 13:12 accels
-rw-r-----  1 josh josh 4750 2009-04-29 17:01 accelsevince
-rw-r-----  1 josh josh 9181 2009-04-30 16:01 accelsgedit
-rw-r-----  1 josh josh 2882 2009-04-28 18:09 backgrounds.xml
drwxr-x---  2 josh josh 4096 2009-02-09 19:18 eog
drwxr-x---  2 josh josh 4096 2009-02-24 15:56 evince
drwxr-x---  2 josh josh 4096 2009-02-08 13:59 file-roller
drwxr-x---  4 josh josh 4096 2009-02-15 19:29 f-spot
drwxr-xr-x  2 josh josh 4096 2009-05-02 15:00 gedit
-rw-r--r--  1 josh josh   74 2009-04-30 16:01 gedit-2
-rw-r-----  1 josh josh 6565 2009-04-30 16:01 gedit-metadata.xml
drwxr-x---  4 josh josh 4096 2009-02-11 16:12 glchess
-rw-r-----  1 josh josh   35 2009-02-11 16:30 gnome-chess
drwxr-x---  2 josh josh 4096 2009-03-28 15:06 gnome-dictionary
-rw-r--r--  1 josh josh   81 2009-04-16 11:58 gnomemeeting
drwxr-x---  2 josh josh 4096 2009-03-13 15:57 gnome-pilot.d
-rw-r-----  1 josh josh   37 2009-03-02 20:22 gnusound
-rw-r-----  1 josh josh   35 2009-03-31 16:08 iagno
drwxr-x---  2 josh josh 4096 2009-03-29 14:08 invest-applet
drwxr-x---  2 josh josh 4096 2009-05-02 13:14 keyrings
drwxr-x---  2 josh josh 4096 2009-02-08 12:35 nautilus-scripts
drwxr-x---  3 josh josh 4096 2009-04-30 16:02 nautilus-sendto
drwxr-x---  3 josh josh 4096 2009-02-08 12:35 panel2.d
drwxr-x---  4 josh josh 4096 2009-04-23 20:56 rhythmbox
drwxr-x---  4 josh josh 4096 2009-02-08 12:35 share
-rw-r--r--  1 josh josh   53 2009-04-20 18:10 Vim
drwxr-x---  2 josh josh 4096 2009-03-09 16:39 wallpapers
-rw-r--r--  1 josh josh   33 2009-04-23 21:28 yelp
``````
~$ ls -la ~/.gnome2_private
total 8
drwx------  2 josh josh 4096 2009-02-08 12:35 .
drwxr-x--- 66 josh josh 4096 2009-05-02 15:36 ..
```

---

