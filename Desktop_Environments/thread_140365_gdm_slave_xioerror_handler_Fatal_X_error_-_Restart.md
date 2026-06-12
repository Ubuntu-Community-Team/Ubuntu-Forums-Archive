---
title: "gdm_slave_xioerror_handler: Fatal X error - Restarting :0"
date: 2006-03-06
forum: Desktop Environments
---

### Post by issueperson on 2006-03-06
HELP!!!
i was messing around with gdesklets and it froze up my desktop.  i had to restart X and when i did, i couldn't log back in to my desktop.
i can run my desktop in gnome failsafe mode, but it freezes up when i try to start a normal gnome session.  
the coresponding syslog is:

localhost gdm[8048] gdm_auth_user_add: /home/brady/.Xauthority is not owned by uid 1001.
localhost gconfd (brady-8907) starting (version 2.12.0), pid 8907 user 'brady'
localhost gconfd (brady-8907) Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (brady-8907) Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
localhost gconfd (brady-8907) Resolved address "xml:readwrite:/home/brady/.gconf" to a writable configuration source at position 2
localhost gconfd (brady-8907) Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
localhost gconfd (brady-8907) Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
localhost gconfd (brady-8907) Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
localhost gconfd (brady-8907) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (brady-8907) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
**localhost gdm[8048] gdm_slave_xioerror_handler: Fatal X error - Restarting :0**
localhost kernel [4294954.714000] mtrr: base(0xc0020000) is not aligned on a size(0x834000) boundary

if anyone can help me, please do.  this is driving me nuts.
(also, i can log in as another user in a regular gnome session.  it's just when i try to log in as brady that it locks up)

---

### Post by DrFunkenstein on 2006-03-06
Simply delete /home/brady/.Xauthority (you'll probably need to use sudo for this) and it should work again.

---

### Post by issueperson on 2006-03-06
that did fix the error about .Xauthority...
it still is freezing at the splashscreen though (before it starts metacity).

error log reads:

localhost gconfd (brady-10273) starting (version 2.12.0), pid 10273 user 'brady'
localhost gconfd (brady-10273) Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
localhost gconfd (brady-10273) Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
localhost gconfd (brady-10273) Resolved address "xml:readwrite:/home/brady/.gconf" to a writable configuration source at position 2
localhost gconfd (brady-10273) Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
localhost gconfd (brady-10273) Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
localhost gconfd (brady-10273) Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
localhost gconfd (brady-10273) Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
localhost gconfd (brady-10273) Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
**localhost gdm[9975] gdm_slave_xioerror_handler: Fatal X error - Restarting :0**
localhost kernel [4296229.972000] mtrr: base(0xc0020000) is not aligned on a size(0x834000) boundary

---

### Post by DrFunkenstein on 2006-03-06
Hm, the only thing I can think off right now, as I really don't have a clue what exactly is going on, is to move all the configuration files for Gnome out of the way and see if this helps. If you are able to start in safe mode, but not in normal mode, I think it's pretty obvious that something is borked in your users config files.

You could try to move the files out of the way one by one, to see if this helps, e.g:
mv .gconf .gconf_bak

and so on.

Hope this helps.

---

### Post by issueperson on 2006-03-06
out of the following files/folders, which ones should i try removing first?  i'm not sure where all the config files are located (i tried removing .gconf, .gconfd and .metacity already which didn't work)

drwx------  45 brady brady   4096 2006-03-06 03:41 .
drwxr-xr-x   6 root  root    4096 2006-02-22 01:43 ..
drwx------   2 brady brady   4096 2006-03-06 01:12 .3ddesktop
-rw-r--r--   1 brady brady  12730 2006-02-23 15:37 915resolution_0.5-2_i386.deb
-rw-r--r--   1 brady brady     24 2006-02-23 13:54 .aspell.en.prepl
-rw-r--r--   1 brady brady     22 2006-02-23 13:54 .aspell.en.pws
-rw-------   1 brady brady   9871 2006-03-06 03:28 .bash_history
-rw-r--r--   1 brady brady    414 2006-02-12 11:17 .bash_profile
-rw-r--r--   1 brady brady   2227 2006-02-12 11:17 .bashrc
drwx------   4 brady brady   4096 2006-02-12 23:32 .config
drwxr-xr-x   2 brady brady   4096 2006-03-06 00:27 Desktop
-rw-------   1 brady brady     16 2006-02-12 11:17 .esd_auth
drwxr-xr-x   7 brady brady   4096 2006-03-06 02:44 .evolution
-rw-r--r--   1 brady brady 112293 2006-02-23 17:32 .fonts.cache-1
drwx------   5 brady brady   4096 2006-03-06 02:52 .gaim
drwxr-xr-x   4 brady brady   4096 2006-02-19 01:41 .galeon
drwx------   7 brady brady   4096 2006-03-06 03:40 .gconf
drwx------   2 brady brady   4096 2006-03-06 03:45 .gconfd
drwxr-xr-x   8 brady brady   4096 2006-03-06 01:19 .gdesklets
drwxr-xr-x  21 brady brady   4096 2006-03-06 00:30 .gimp-2.2
-rw-r-----   1 brady brady      0 2006-03-06 03:30 .gksu.lock
drwxr-xr-x   5 brady brady   4096 2006-02-22 02:41 .gnome
drwx------  15 brady brady   4096 2006-03-06 03:39 .gnome2
drwx------   2 brady brady   4096 2006-02-12 15:52 .gnome2_private
srwxr-xr-x   1 brady brady      0 2006-03-06 00:47 .gnome-system-monitor.brady
drwx------   2 brady brady   4096 2006-02-13 01:27 .gpilotd
-rw-r--r--   1 brady brady      5 2006-03-03 13:31 .gpilotd.pid
drwxr-xr-x   2 brady brady   4096 2006-02-12 19:15 .gstreamer-0.8
-rw-r--r--   1 brady brady     87 2006-02-28 16:17 .gtkrc-1.2-gnome2
-rw-r--r--   1 brady brady     32 2006-03-05 19:07 .hwdb
-rw-------   1 brady brady   9328 2006-03-06 03:40 .ICEauthority
drwxr-xr-x  14 brady brady   4096 2006-03-05 17:00 .icons
drwxr-xr-x   3 brady brady   4096 2006-02-14 02:12 .java
drwx------   3 brady brady   4096 2006-02-15 15:16 .kde
drwx------   3 brady brady   4096 2006-02-20 20:46 .keytouch2
drwxr-xr-x   3 brady brady   4096 2006-02-12 23:32 .local
drwx------   3 brady brady   4096 2006-02-14 01:51 .macromedia
-rw-r--r--   1 brady brady   2094 2006-02-14 17:47 .mailcap
drwxr-xr-x   3 brady brady   4096 2006-02-15 15:24 .mcop
-rw-------   1 brady brady     31 2006-02-16 17:30 .mcoprc
drwxr-xr-x   2 brady brady   4096 2006-02-13 02:01 Media
drwx------   4 brady brady   4096 2006-02-13 22:01 .mozilla
drwxr-xr-x  24 brady brady   4096 2006-03-05 00:59 Music
drwxr-xr-x   3 brady brady   4096 2006-02-12 11:17 .nautilus
drwx------   3 brady brady   4096 2006-03-03 16:17 .openoffice.org2
drwxr-xr-x   2 brady brady   4096 2006-03-05 17:42 Pictures
drwxr-xr-x   2 brady brady   4096 2006-02-15 15:16 .qt
-rw-------   1 brady brady  60812 2006-03-06 02:44 .recently-used
drwxr-xr-x   5 brady brady   4096 2006-03-03 13:19 School
drwxr-xr-x   2 brady brady   4096 2006-03-04 17:37 .serpentine
-rw-------   1 brady brady     50 2006-02-13 22:36 .serverauth.11188
srwxr-xr-x   1 brady brady      0 2006-03-01 17:21 .sound-juicer.brady
drwxr-xr-x  10 brady brady   4096 2006-03-05 16:34 .themes
drwx------   4 brady brady   4096 2006-02-12 14:19 .thumbnails
drwx------   4 brady brady   4096 2006-03-06 03:23 .Trash
drwx------   2 brady brady   4096 2006-02-18 17:05 .update-notifier
-rw-------   1 brady brady    918 2006-02-22 13:13 .viminfo
drwx------   2 brady brady   4096 2006-02-19 02:58 .w3m
drwxr-xr-x   4 brady brady   4096 2006-02-27 12:16 .wine
drwxrwxrwx   3 brady brady   4096 2006-02-20 19:29 .xbindkeys_config
-rw-r--r--   1 brady brady   1107 2006-02-20 20:38 .xbindkeysrc
drwxr-xr-x   2 brady brady   4096 2006-02-27 21:14 .xbl-scores
drwxr-xr-x   2 brady brady   4096 2006-02-16 01:10 .xine
-rw-r--r--   1 brady brady  11186 2006-02-28 14:03 .xscreensaver
-rw-r--r--   1 brady brady   1468 2006-03-06 03:40 .xsession-errors

---

### Post by DrFunkenstein on 2006-03-06
Hm, you should also try the .gnome* directorys. IIRC that's where the sessions are saved.

---

### Post by issueperson on 2006-03-06
fixed.  thanks for all your help.

for the record, the broken file was somewhere in the ~/.gnome2 directory.  i'm gonna try to recover some of my config files from my old setup 'cause i had a lot of work go into setting it up.  i'll update if i figure out which file it was that screwed everything up.

issueperson


[B]UPDATE:  i restored it all the way it was except for two files:

~/.gnome2/session
~/.gnome2/session-manual

and it works.  so one of those two files boogered up the whole system.[/B]

---

