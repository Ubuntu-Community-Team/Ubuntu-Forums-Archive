---
title: "Permissions problems after reinstall"
date: 2009-06-08
forum: General Help
---

### Post by lariosa42 on 2009-06-08
Hello,

I recently reinstalled Ubuntu, and copied my old [FONT="Courier New"]/home[/FONT] directory over my new one, but none of my preferences are working (e.g. Firefox doesn't have my old bookmarks.)  After looking around the Forums and Googling a bit, it seems that maybe something like this:
```

sudo chown -R USER:USER /home/USER/
sudo chmod -R 664 /home/USER

```
might work, but I am hesitant to try this (especially since my /home folder is about 80 G).

Can anyone provide some insight into this?  Will it restore my settings?  Is it too restrictive?  Is there something else I should do?  Also, can anyone give a resource that discusses what the different permission numbers are (e.g. 664, 770, etc.)?  Thank you for your help!

---

### Post by michy99 on 2009-06-08
Before you do that, what is the output of```
ls -l /home
```

---

### Post by lariosa42 on 2009-06-08
Thanks for the quick response.  [FONT="Courier New"]ls -l /home[/FONT] gives

```
drwx------ 127 adam adam 12288 2009-06-08 16:20 adam
```

Also, I was able to find an answer my question about the [FONT="Courier New"]chmod[/FONT] numbers [here]("http://ubuntuforums.org/archive/index.php/t-138356.html").  In case anyone is interested, they translate as:


user
read write execute
400 200 100

group
read write execute
40 20 10

other
read write execute
4 2 1

and you just add the numbers up.

---

### Post by michy99 on 2009-06-08
Okay your home directory is owned by you, so that is right, but the permissions are off. You have read, write and execute privileges but group and others have no privileges. Group and others should have read and execute but not write. So you should```
chmod 755 /home/adam
```

---

### Post by lariosa42 on 2009-06-08
OK, I executed [FONT="Courier New"]chmod 755 /home/adam[/FONT] and restarted, but it is still not recognizing my settings.  Do I need to recursively [FONT="Courier New"]chmod[/FONT] on /home/USER?  If so, what permission level should I use?

---

### Post by michy99 on 2009-06-08
That's a tricky one. Looking in my home directory, not everything has the same permissions. Most are owned by me with me as group, but some have root as group. Most have 755 permissions but there are a lot of exceptions also. I do know that .gvfs has to be set to 500. Do a```
ls -la
``` in your home directory and see what it looks like.

---

### Post by lariosa42 on 2009-06-08
Hey michy, here is the output of [FONT="Courier New"]ls -la[/FONT]

```

drwxr-xr-x 127 adam adam     12288 2009-06-08 17:49 .
drwxr-xr-x   3 root root      4096 2009-06-07 19:49 ..
drwxrwxrwx   5 adam adam      4096 2009-02-28 11:56 .adobe
drwxrwxrwx   2 adam adam      4096 2009-02-08 11:24 .amazonmp3
drwxrwxrwx   2 adam adam      4096 2009-05-04 15:52 .aptitude
-rwxrwxrwx   1 adam adam       188 2008-12-01 02:21 .asoundrc
-rwxrwxrwx   1 adam adam       305 2008-12-01 02:21 .asoundrc.asoundconf
-rwxrwxrwx   1 adam adam        24 2008-06-14 15:14 .aspell.en.prepl
-rwxrwxrwx   1 adam adam        22 2008-06-14 15:14 .aspell.en.pws
-rwxrwxrwx   1 adam adam       176 2008-06-13 23:57 .barrage.hscr
-rwxrwxrwx   1 adam adam        11 2008-11-06 10:51 .bash_aliases
-rwxrwxrwx   1 adam adam     12905 2009-06-08 17:48 .bash_history
-rw-rw-rw-   1 adam adam       220 2009-06-07 19:49 .bash_logout
-rw-rw-rw-   1 adam adam      3115 2009-06-07 19:49 .bashrc
-rwxrwxrwx   1 adam adam      3032 2008-10-16 12:10 .bashrc~
-rwxrwxrwx   1 adam adam      3004 2009-05-31 13:19 .bashrc.save
-rwxrwxrwx   1 adam adam        81 2008-12-24 15:51 .BillardGL.conf.v7
-rwxrwxrwx   1 adam adam      1480 2009-04-04 00:54 .BOINC Manager
-rwxrwxrwx   1 adam adam       112 2008-06-13 23:17 .bugsquish
drwxrwx---   5 adam adam      4096 2009-06-07 23:39 .cache
-rwxrwxrwx   1 adam adam      3456 2008-09-14 19:35 .cgobanrc
drwxrwxrwx  12 adam adam      4096 2009-03-19 10:50 compiz
drwxrwx---   3 adam adam      4096 2009-06-07 21:10 .compiz
-rwxrwxrwx   1 adam adam     28360 2009-04-19 11:51 compiz-check
drwxrwxrwx   4 adam adam      4096 2009-03-19 10:52 compiz-switch-0.2.0~source
drwxrwxrwx   5 adam adam      4096 2009-06-07 21:20 .config
drwxrwxrwx   2 adam adam      4096 2008-09-18 00:41 .critter
drwxrwxrwx   2 adam adam      4096 2009-04-13 10:03 .cups
drwxrwxrwx   3 adam adam      4096 2009-06-07 12:52 .dbus
drwxrwxrwx   4 adam adam      4096 2009-02-23 09:24 .ddd
drwxrwxrwx   2 adam adam      4096 2009-04-25 13:30 .debtags
drwxrwxrwx  11 adam adam      4096 2009-06-08 15:57 Desktop
-rw-r--r--   1 adam adam        47 2009-06-08 17:49 .dmrc
-rw-r--r--   1 adam adam        47 2009-06-08 18:03 .dmrc~
drwxrwxrwx   3 adam adam      4096 2009-06-07 20:04 Documents
drwxrwxrwx   6 adam adam      4096 2009-02-01 08:49  dot googleearth
drwxrwxrwx   5 adam adam      4096 2009-05-11 19:15 .dvdcss
drwxrwxrwx   2 adam adam      4096 2008-12-06 14:34 dwhelper
drwxrwxrwx   2 adam adam      4096 2009-01-13 22:42 .easytag
drwxrwxrwx   2 adam adam      4096 2009-03-27 21:09 emacs
-rwxrwxrwx   1 adam adam      1480 2009-03-27 21:33 .emacs
-rwxrwxrwx   1 adam adam      1414 2009-03-27 18:42 .emacs~
drwxrwxrwx   4 adam adam      4096 2009-02-21 18:30 .emacs.d
-rwxrwxrwx   1 adam adam        36 2009-02-21 18:43 .emacs-places
-rwxrwxrwx   1 adam adam     12288 2009-02-21 18:34 .emacs.swp
drwxrwxrwx   2 adam adam      4096 2008-06-16 10:05 .emilia
drwxrwxrwx   5 adam adam      4096 2008-06-16 22:21 .enigma
-rwxrwxrwx   1 adam adam       866 2008-06-16 22:21 .enigmarc.xml
-rwxrwxrwx   1 adam adam         0 2008-11-01 21:50 en_US.UTF-8
-rw-rw-rw-   1 adam adam        16 2009-06-07 12:52 .esd_auth
drwxrwxrwx   8 adam adam      4096 2008-10-30 18:07 .evolution
-rw-rw-rw-   1 adam adam       357 2009-06-07 19:49 examples.desktop
drwxrwxrwx   7 adam adam      4096 2008-06-13 19:16 .fceultra
drwxrwxrwx   8 adam adam      4096 2009-04-21 13:30 .fceux
-rwxrwxrwx   1 adam adam       863 2008-12-12 20:26 fig3
drwxrwxrwx   4 adam adam      4096 2008-06-13 23:26 .fillets-ng
drwxrwxrwx  13 adam adam      4096 2008-05-29 13:21 firefox
-rwxrwxrwx   1 adam adam   1436607 2009-05-24 01:45 Firefox_wallpaper.png
-rwxrwxrwx   1 adam adam        56 2008-11-13 11:16 .flexlmrc
drwxrwxr-x   2 adam adam      4096 2009-06-07 12:52 .fontconfig
drwxrwxrwx   2 adam adam      4096 2008-10-05 20:28 .gcjwebplugin
drwxrwxrwx   5 adam adam      4096 2009-06-08 17:49 .gconf
drwxrwxrwx   2 adam adam      4096 2009-06-08 17:56 .gconfd
-rwxrwxrwx   1 adam adam    169533 2009-03-17 22:12 GDM-GreenForest.tar.gz
-rwxrwxrwx   1 adam adam     29932 2009-05-18 15:15 gedit
drwxrwxrwx   4 adam adam      4096 2008-11-21 14:10 .gegl-0.0
drwxrwxrwx   2 adam adam      4096 2008-06-13 19:14 .gfceu
-rwxrwxrwx   1 adam adam       459 2009-05-15 11:36 .gfceugfceu_options.dat
-rwxrwxrwx   1 adam adam         0 2009-06-08 13:59 .gksu.lock
-rwxrwxrwx   1 adam adam       418 2009-04-28 20:20 .glade2
drwxrwxrwx   4 adam adam      4096 2008-06-15 08:49 .gnome
drwxrwxrwx  10 adam adam      4096 2009-06-08 17:48 .gnome2
drwxrwx---   2 adam adam      4096 2009-06-07 12:52 .gnome2_private
drwxrwxrwx   2 adam adam      4096 2009-06-07 12:52 .gnupg
drwxrwxrwx   4 adam adam      4096 2009-01-07 16:26 GNUstep
drwxrwxrwx   3 adam adam      4096 2009-04-17 22:53 .google
drwxrwxrwx   4 adam adam      4096 2009-05-15 11:16 .googleearth
drwxrwxrwx   3 adam adam      4096 2008-06-13 23:28 .gPlanarity
drwxrwxr-x   2 adam adam      4096 2009-06-07 23:22 .gstreamer-0.10
-rw-r--r--   1 adam adam       144 2009-06-08 17:49 .gtk-bookmarks
drwxrwxrwx   3 adam adam      4096 2008-10-31 19:51 .gtkpod
-rwxrwxrwx   1 adam adam        25 2008-11-12 00:45 .gtkrc-2.0.save
dr-x------   2 adam adam         0 2009-06-08 17:49 .gvfs
drwxrwxrwx   2 adam adam      4096 2008-09-02 10:59 .hplip
-rwxrwxrwx   1 adam adam     27824 2008-10-10 22:18 hs_err_pid12561.log
-rwxrwxrwx   1 adam adam     26462 2008-11-02 13:12 hs_err_pid15064.log
-rwxrwxrwx   1 adam adam     27980 2008-11-13 11:24 hs_err_pid9533.log
-rw-------   1 adam adam      1183 2009-06-08 17:49 .ICEauthority
-rwxrwxrwx   1 adam adam       466 2009-01-06 14:26 ICMS app~
-rwxrwxrwx   1 adam adam         0 2009-03-17 23:51 ICON-NoiaWarm.tar.bz2
drwxrwxr-x   2 adam adam      4096 2009-06-07 21:19 .icons
drwxrwxrwx   2 adam adam      4096 2008-11-04 18:39 Icons
-rwxrwxrwx   1 adam adam         0 2009-03-17 21:45 ICON-SmoothGNOME.tar.gz
drwxrwxrwx   7 adam adam      4096 2009-03-15 18:24 .inkscape
-rwxrwxrwx   1 adam adam        45 2009-03-20 02:19 .ispell_default
drwxrwxrwx   4 adam adam      4096 2008-11-01 14:05 .java
-rwxrwxrwx   1 adam adam     32505 2008-10-10 22:18 java.log.12561
-rwxrwxrwx   1 adam adam     32618 2008-11-05 03:02 java.log.1287
-rwxrwxrwx   1 adam adam     36338 2008-11-05 04:14 java.log.15195
-rwxrwxrwx   1 adam adam        68 2008-12-09 20:19 java.log.8792
drwxrwxrwx  75 adam adam      4096 2008-12-23 14:57 JM
drwxrwxrwx   2 adam adam      4096 2008-09-09 23:09 .jmol
-rwxrwxrwx   1 adam adam    403870 2008-10-14 11:43 Jmol.pov
-rwxrwxrwx   1 adam adam       387 2008-10-14 11:43 Jmol.pov.ini
-rwxrwxrwx   1 adam adam      7732 2008-10-14 11:43 Jmol.pov.spt
drwxrwxrwx   4 adam adam      4096 2008-10-20 09:02 .kde
drwxrwxrwx   3 adam adam      4096 2008-06-15 00:20 .kde4
drwxrwxrwx   6 adam adam      4096 2009-05-17 20:30 kile-2.0.3
-rwxrwxrwx   1 adam adam        35 2008-09-11 22:37 .lesshst
-rwxrwxrwx   1 adam adam        27 2008-12-01 02:21 .libao
drwxrwxrwx   2 adam adam      4096 2009-04-25 11:43 .libgda
-rwxrwxrwx   1 adam adam    668580 2008-07-28 14:06 libpoppler2_0.6-0ubuntu2.3_i386.deb
-rwxrwxrwx   1 adam adam     87037 2009-03-22 12:51 .libquicktime_codecs
-rwxrwxrwx   1 adam adam      1213 2009-04-04 00:49 .liquidwarrc
drwxrwxrwx   4 adam adam      4096 2008-09-01 14:46 .listen
drwxrwxrwx   3 adam adam      4096 2008-06-11 20:12 .local
drwxrwxrwx   2 adam adam      4096 2009-05-09 12:56 Log Files
-rwxrwxrwx   1 adam adam       812 2008-11-24 01:44 log.txt
drwxrwxrwx   3 adam adam      4096 2008-06-15 08:49 .loki
-rwxrwxrwx   1 adam adam      1096 2008-12-23 05:49 .lordsawarrc
-rwxrwxrwx   1 adam adam       954 2008-12-21 14:10 .lordsawarrc.OLD
drwxrwxrwx  34 adam adam      4096 2009-05-20 22:23 .lyrics
drwxrwxrwx  13 adam adam      4096 2009-05-28 17:16 .lyx
drwxrwxrwx   3 adam adam      4096 2008-06-11 21:27 .macromedia
-rwxrwxrwx   1 adam adam        35 2008-12-21 14:13 .Maelstrom-data
drwxrwxrwx   3 adam adam      4096 2008-11-13 11:17 .maple
drwxrwxrwx   9 adam adam      4096 2008-11-13 11:24 .Mathematica
drwxrwxrwx  16 adam adam      4096 2008-12-05 15:56 matlab
drwxrwxrwx   3 adam adam      4096 2008-12-03 16:18 .matlab
-rwxrwxrwx   1 adam adam         0 2009-04-24 18:30 matlab_crash_dump.17668
-rwxrwxrwx   1 adam adam      1349 2008-12-07 08:28 MATLABDesktopSaveError.log
drwxrwxrwx   3 adam adam      4096 2008-06-12 04:22 .mcop
-rwxrwxrwx   1 adam adam        31 2008-06-14 15:16 .mcoprc
drwxrwxrwx   3 adam adam      4096 2008-06-15 11:31 .metacity
-rw-r--r--   1 adam adam       248 2009-06-08 13:52 MountISO
drwxrwx---   4 adam adam      4096 2009-06-07 12:55 .mozilla
drwxrwxrwx   6 adam adam      4096 2008-10-30 20:02 .mozilla_backup
-rwxrwxrwx   1 adam adam   2702003 2009-02-15 17:42 mozilla.ps
drwxrwxrwx   3 adam adam      4096 2008-06-12 03:17 .mozilla-thunderbird
drwxrwxrwx   2 adam adam      4096 2009-05-14 12:00 .mplayer
drwxrwxrwx   4 adam adam      4096 2009-05-04 18:16 .mupen64plus
drwxrwxrwx 548 adam adam     20480 2009-06-08 09:51 Music
-rwxrwxrwx   1 adam adam         1 2008-11-06 10:15 myfile.txt~
drwxrwxr-x   3 adam adam      4096 2009-06-07 12:52 .nautilus
drwxrwxrwx   3 adam adam      4096 2008-08-19 14:00 .netx
-rwxrwxrwx   1 adam adam        54 2008-08-19 14:00 .netxrc
drwxrwxrwx   3 adam adam      4096 2008-08-14 19:13 .nexuiz
drwxrwxrwx   2 adam adam      4096 2009-04-19 12:09 nocompiz
-rwxrwxrwx   1 adam adam 595144100 2008-12-07 08:44 nohup.out
-rwxrwxrwx   1 adam adam        64 2008-11-18 13:56 .octave_hist
drwxrwxrwx   9 adam adam      4096 2009-05-15 16:40 .openarena
drwxrwxrwx   3 adam adam      4096 2009-03-22 12:52 .openme
-rwxrwxrwx   1 adam adam       399 2009-03-22 13:10 .openme.prefs
-rwxrwxrwx   1 adam adam        71 2009-03-22 13:03 .openme.presets
drwxrwxrwx   2 adam adam      4096 2008-06-16 12:15 .orbit
drwxrwxrwx   3 adam adam      4096 2008-06-20 16:36 .parallelrealities
drwxrwxrwx   2 adam adam      4096 2009-04-10 23:03 Photos
drwxrwxrwx   2 adam adam      4096 2008-09-14 17:35 Pictures
drwxrwxrwx   5 adam adam      4096 2008-06-16 21:43 .pokerth
drwxrwxrwx   2 adam adam      4096 2008-06-14 23:44 .ppracer
-rwxrwxrwx   1 adam adam        37 2009-04-26 15:19 .printer-groups.xml
-rw-rw-rw-   1 adam adam       675 2009-06-07 19:49 .profile
drwxrwxrwx   2 adam adam      4096 2009-06-07 12:52 Public
drwx------   2 adam adam      4096 2009-06-08 17:49 .pulse
-rw-rw-rw-   1 adam adam       256 2009-06-07 12:52 .pulse-cookie
drwxrwxrwx   4 adam adam      4096 2008-11-23 10:49 .purple
-rwxrwxrwx   1 adam adam        78 2008-09-18 11:40 .pychessconf
-rwxrwxrwx   1 adam adam     53898 2009-05-08 10:04 .recently-used
-rw-------   1 adam adam     86421 2009-06-08 17:48 .recently-used.xbel
-rwxrwxrwx   1 adam adam   1600903 2009-05-17 18:28 .recently-used.xbel.6RVKUU
-rwxrwxrwx   1 adam adam   1862142 2009-06-04 10:49 .recently-used.xbel.7DX1UU
-rwxrwxrwx   1 adam adam   1859788 2009-06-01 18:33 .recently-used.xbel.A1IRUU
-rwxrwxrwx   1 adam adam   1859584 2009-06-04 20:12 .recently-used.xbel.AKU1UU
-rwxrwxrwx   1 adam adam   1583447 2009-05-17 18:23 .recently-used.xbel.D2SKUU
-rwxrwxrwx   1 adam adam   1859788 2009-06-01 18:33 .recently-used.xbel.HOIPUU
-rwxrwxrwx   1 adam adam   1866105 2009-05-20 11:53 .recently-used.xbel.NPM3TU
-rwxrwxrwx   1 adam adam   1858838 2009-06-03 17:34 .recently-used.xbel.S4UPUU
-rwxrwxrwx   1 adam adam   1880091 2009-05-27 08:52 .recently-used.xbel.U355TU
drwxrwxrwx   2 adam adam      4096 2009-04-12 18:00 Referencer
-rwxrwxrwx   1 adam adam       237 2009-06-03 01:11 .registry
drwxrwxrwx   9 adam adam      4096 2008-10-12 13:27 sage-3.0.6-i686-Linux
drwxrwxrwx   3 adam adam      4096 2008-06-26 10:03 .sane
drwxrwxrwx   2 adam adam      4096 2008-09-15 17:07 .scummvm
-rwxrwxrwx   1 adam adam        97 2008-12-23 05:25 .scummvmrc
drwxrwxrwx   4 adam adam      4096 2008-11-23 11:17 .Skype
drwxrwxrwx   3 adam adam      4096 2008-12-10 08:02 Skype settings
drwxrwxrwx  15 adam adam      4096 2009-05-20 22:36 Songbird
drwxrwxrwx   4 adam adam      4096 2009-03-17 13:40 .songbird2
drwxrwxrwx   2 adam adam      4096 2009-01-12 00:15 src
drwxrwxrwx   2 adam adam      4096 2008-10-01 23:09 .ssh
drwxrwxrwx   2 adam adam      4096 2008-06-16 11:22 .stellarium
-rwxrwxrwx   1 adam adam         0 2008-06-11 20:46 .sudo_as_admin_successful
drwxrwxrwx   3 adam adam      4096 2008-09-20 16:57 .supertux2
-rwxrwxrwx   1 adam adam     53248 2009-05-18 15:17 .swo
-rwxrwxrwx   1 adam adam     28672 2009-05-06 23:07 .swp
drwxrwxrwx   2 adam adam      4096 2009-06-07 12:52 Templates
-rwxrwxrwx   1 adam adam       793 2008-11-06 10:07 Terminal Commands~
drwxrwxrwx   3 adam adam      4096 2008-10-16 12:17 texmf
drwxrwxr-x   2 adam adam      4096 2009-06-07 21:19 .themes
drwxrwxrwx   3 adam adam      4096 2009-04-25 13:13 Themes
drwxrwx---   4 adam adam      4096 2009-06-08 12:24 .thumbnails
drwxrwxrwx   5 adam adam      4096 2009-05-13 22:12 .tomboy
-rwxrwxrwx   1 adam adam      4471 2009-06-05 10:35 .tomboy.log
drwxrwxrwx   5 adam adam      4096 2008-09-14 14:31 .transmission
drwxrwxrwx   2 adam adam      4096 2008-06-12 12:36 .tsclient
-rwxrwxrwx   1 adam adam        34 2008-06-14 23:29 .tuxpuckrc
drwxrwxr-x   2 adam adam      4096 2009-06-07 20:12 .update-manager-core
drwxrwx---   2 adam adam      4096 2009-06-07 12:52 .update-notifier
drwxrwxrwx   4 adam adam      4096 2008-10-13 23:14 .uqm
-rwxrwxrwx   1 adam adam      1212 2009-03-24 15:38 .usb-creator.log
drwxrwxrwx   2 adam adam      4096 2009-03-22 13:05 Video Projects
drwxrwxrwx   2 adam adam      4096 2008-09-14 17:35 Videos
drwxrwxrwx   4 adam adam      4096 2009-02-18 10:02 .VirtualBox
drwxrwxrwx   2 adam adam      4096 2009-04-29 11:43 .w3m
drwxrwxrwx   2 adam adam      4096 2009-06-04 21:22 .wapi
drwxrwxrwx   2 adam adam      4096 2008-11-01 21:56 Webpage
drwxrwxrwx   2 adam adam      4096 2008-06-16 16:06 .winefish
drwxrwxrwx   2 adam adam      4096 2008-10-24 07:50 .workrave
-rwxrwxrwx   1 adam adam       122 2009-06-05 10:33 .Xauthority
drwxrwxrwx   3 adam adam      4096 2008-11-06 09:57 .xbindkeys_config
-rwxrwxrwx   1 adam adam      1136 2008-12-03 17:16 .xbindkeysrc
-rwxrwxrwx   1 adam adam      1458 2009-05-04 08:01 .xdvirc
drwxrwxrwx   2 adam adam      4096 2008-09-19 21:50 .xine
drwxrwxrwx   4 adam adam      4096 2009-02-07 12:14 .xmms
-rwxrwxrwx   1 adam adam       129 2008-11-11 11:40 .xscreensaver-getimage.cache
-rw-r--r--   1 adam adam      4823 2009-06-08 17:50 .xsession-errors
drwxrwxrwx   2 adam adam      4096 2009-02-20 18:29 .zsnes

```

---

### Post by michy99 on 2009-06-08
Apparently whatever method you used to backup your files did not preserve the permissions. I'm comparing your list with mine and I'll get back in a little while.

---

### Post by lariosa42 on 2009-06-08
Thank you.  I look forward to your reply.  Would you mind posting your ls -la output so that I can see what a 'healthy' one looks like?

Many thanks again for your help.

---

### Post by michy99 on 2009-06-08
Okay, here is what mine looks like.```
total 4396364
drwxr-xr-x 103 mike mike      12288 2009-06-08 20:38 .
drwxr-xr-x   4 root root       4096 2009-04-13 04:33 ..
drwxr-xr-x   2 mike mike       4096 2009-02-18 15:19 .abe
drwxr-xr-x   3 mike root       4096 2009-01-16 13:00 .adobe
drwxr-xr-x   2 mike mike       4096 2009-06-02 16:32 .alex4
drwxr-xr-x   4 mike mike       4096 2009-05-27 20:55 .aMule
drwx------   3 mike mike       4096 2009-05-05 10:36 .appdata
drwxr-xr-x   4 mike mike       4096 2009-05-01 14:54 .avg7
drwxr-xr-x   3 mike root       4096 2009-05-25 14:56 .avidemux
-rw-r--r--   1 mike mike        106 2009-06-04 23:35 .ballz_saves.txt
-rwxr-xr-x   1 mike mike      10566 2009-06-07 22:53 .bash_history
-rwxr-xr-x   1 mike mike        220 2009-01-16 11:37 .bash_logout
-rwxr-xr-x   1 mike mike       3131 2009-05-06 09:44 .bashrc
-rw-r--r--   1 mike mike       2983 2009-04-24 22:21 .bashrc~
drwxr-xr-x   2 mike mike       4096 2009-05-31 08:14 bin
drwxr-xr-x   2 mike root       4096 2009-01-16 13:00 .bogofilter
drwxr-xr-x   8 mike root       4096 2009-05-29 17:18 .cache
drwxr-xr-x  18 mike root       4096 2009-05-28 15:43 .config
-rw-r--r--   1 mike mike         99 2009-05-05 22:49 Convert wmv to avi
-rw-r--r--   1 mike mike          1 2009-05-05 22:48 Convert wmv to avi~
-rwxr-xr-x   1 mike mike        191 2009-05-13 22:06 .crossword.cfg
drwxr-xr-x   2 mike root       4096 2009-05-10 19:16 .crossword_puzzles
drwx------   3 mike mike       4096 2009-05-27 18:10 .dbus
drwxr-xr-x   7 mike root       4096 2009-06-08 20:36 Desktop
-rw-r--r--   1 mike mike         56 2009-02-02 14:01 .devede
drwxr-xr-x   3 mike mike       4096 2004-05-20 15:20 diveintopython-5.4
-rw-------   1 mike mike         28 2009-06-08 09:10 .dmrc
drwxr-xr-x   7 mike root       4096 2009-05-18 13:08 Documents
drwxr-xr-x  25 mike root       4096 2009-05-30 13:42 .dvdcss
-rw-r--r--   1 mike mike      27568 2009-04-28 09:34 dvds.ctg
drwxr-xr-x   2 mike mike       4096 2009-05-28 06:31 dwhelper
drwxr-xr-x   3 mike root       4096 2009-01-16 11:37 .einstein
-rw-------   1 mike mike 4294967296 2009-05-11 09:16 end
-rwxr-xr-x   1 mike mike         16 2009-01-16 11:38 .esd_auth
drwxr-xr-x   7 mike mike       4096 2009-06-08 09:16 .evolution
drwxr-xr-x   8 mike mike       4096 2009-06-06 09:29 evolutionback
lrwxrwxrwx   1 mike mike         26 2009-01-16 11:37 Examples -> /usr/share/example-content
drwxrwxrwx   4 mike mike       4096 2009-05-23 23:19 ext3grep-0.10.1
-rw-r--r--   1 mike mike        976 2009-05-16 19:56 f
-rw-r--r--   1 mike mike       2366 2009-05-30 09:18 .fehrc
drwxr-xr-x   7 mike mike       4096 2009-06-05 12:00 Foldit
drwxr-xr-x   2 mike root       4096 2009-06-03 18:54 .fontconfig
drwxr-xr-x   6 mike mike       4096 2009-03-02 08:13 freenet
drwxr-xr-x   6 mike root       4096 2009-06-08 09:30 .gconf
drwxr-xr-x   2 mike root       4096 2009-06-08 20:21 .gconfd
drwx------   4 mike mike       4096 2009-05-28 11:59 .gegl-0.0
drwxr-xr-x  22 mike root       4096 2009-05-24 23:40 .gimp-2.4
drwxr-xr-x  22 mike mike       4096 2009-06-07 15:40 .gimp-2.6
-rwxr-xr-x   1 mike mike          0 2009-06-08 17:00 .gksu.lock
drwxr-xr-x   5 mike root       4096 2009-05-30 22:09 .gnome
drwxr-xr-x  23 mike root       4096 2009-06-07 22:54 .gnome2
drwxr-xr-x   2 mike mike       4096 2009-01-16 11:38 .gnome2_private
drwx------   3 mike mike       4096 2009-05-29 18:27 .gnome-color-chooser
-rw-r--r--   1 mike mike        984 2009-04-27 22:08 .gnome-hearts.cfg
drwx------   2 mike mike       4096 2009-01-16 11:37 .gnome_private
drwxr-xr-x   4 mike root       4096 2009-01-16 11:37 .gnucash
drwxr-xr-x   5 mike mike       4096 2009-05-27 16:21 .gnunet
drwxr-xr-x   2 mike root       4096 2009-05-28 00:34 .gnupg
drwxr-xr-x   4 mike mike       4096 2009-01-20 21:13 GNUstep
drwxr-xr-x   2 mike mike       4096 2009-01-16 11:37 .gpilotd
-rwxr-xr-x   1 mike mike          4 2009-01-16 11:37 .gpilotd.pid
-rwxr-xr-x   1 mike mike        157 2009-05-16 15:23 .gprename
-rwxr-xr-x   1 mike mike      35798 2009-05-16 15:21 .gprename_log
-rwxr-xr-x   1 mike mike       4016 2009-01-16 11:37 .grisbirc
drwxr-xr-x   2 mike root       4096 2009-05-29 16:31 .gstreamer-0.10
-rw-r--r--   1 mike mike        104 2009-06-08 14:30 .gtk-bookmarks
-rw-r--r--   1 mike mike         41 2009-06-01 11:28 .gtkrc-2.0
-rw-r--r--   1 mike mike       2612 2009-06-01 11:28 .gtkrc-2.0-gnome-color-chooser
dr-x------   2 mike mike          0 2009-06-08 09:10 .gvfs
drwxr-xr-x   2 mike root       4096 2009-01-16 11:37 .gwhere
drwxr-xr-x   2 mike root       4096 2009-01-16 11:37 .hplip
drwxr-xr-x  17 mike mike       4096 2009-05-28 02:41 i2p
-rw-------   1 mike mike       6680 2009-06-08 09:10 .ICEauthority
drwxr-xr-x   2 mike mike       4096 2009-01-16 13:00 .icons
drwxr-xr-x   4 mike mike       4096 2009-05-28 02:42 .iMule
-rw-------   1 mike mike   22487201 2009-06-05 11:18 Inbox
-rwxr-xr-x   1 mike mike        173 2009-01-16 11:37 index.html
drwxr-xr-x   4 mike root       4096 2009-01-16 11:38 .java
drwxr-xr-x  12 mike mike       4096 2009-05-19 21:26 .jd
-rwxr-xr-x   1 mike mike       1676 2009-02-18 21:06 jd.sh
drwx------   3 mike mike       4096 2009-01-16 17:05 .kde
drwxr-xr-x   3 mike root       4096 2009-01-16 11:37 .kde4
-rw-r--r--   1 mike mike    1126684 2009-05-14 16:31 KG.jpg
-rw-r--r--   1 mike mike        756 2009-04-10 19:03 .lincityrc
-rw-r--r--   1 mike mike        289 2009-02-21 17:15 lint.txt
drwxr-xr-x   5 mike mike       4096 2009-04-19 17:00 lmms
-rw-r--r--   1 mike mike       2087 2009-05-29 16:07 .lmmsrc.xml
drwxr-xr-x   3 mike root       4096 2009-01-16 11:37 .local
drwxr-xr-x   3 mike root       4096 2009-01-16 11:37 .macromedia
-rw-r--r--   1 mike mike        339 2009-02-25 01:11 mathsymbols
-rw-r--r--   1 mike mike        171 2009-02-14 12:57 mathsymbols~
drwxr-xr-x   3 mike mike       4096 2009-01-16 17:07 .mcop
-rw-------   1 mike mike         31 2009-01-16 21:49 .mcoprc
drwxr-xr-x   3 mike root       4096 2009-01-16 11:37 .metacity
drwxr-xr-x   6 mike root       4096 2009-04-24 10:56 .mozilla
-rwxr-xr-x   1 mike mike      81270 2009-01-16 13:00 mozilla.ps
drwxr-xr-x   2 mike root       4096 2009-01-16 11:37 .mplayer
drwxr-xr-x   2 mike mike       4096 2009-01-16 11:38 Music
drwxr-xr-x   3 mike root      20480 2009-05-27 15:16 .nautilus
drwxr-xr-x   7 mike mike       4096 2009-04-26 18:08 .nbi
drwxr-xr-x   4 mike mike       4096 2009-04-26 20:14 .netbeans
drwxr-xr-x  13 mike mike       4096 2009-04-26 18:07 netbeans-6.5.1
drwxr-xr-x   3 mike mike       4096 2009-04-26 20:16 .netbeans-derby
drwxr-xr-x   9 mike mike       4096 2009-05-02 06:50 NetBeansProjects
drwxr-xr-x   4 mike mike       4096 2009-04-26 18:07 .netbeans-registration
-rwxr-xr-x   1 mike mike     336469 2009-01-16 11:37 nov08tax.pdf
drwxr-xr-x   4 mike mike       4096 2009-05-11 15:32 openkremlin-b255ad38a92f
drwxr-xr-x   3 mike mike       4096 2009-04-21 12:59 .openoffice.org
drwxr-xr-x   3 mike root       4096 2009-04-21 12:26 .openoffice.org2
-rw-r--r--   1 root root      35334 2009-05-05 11:47 packagelist
drwxr-xr-x   4 mike mike       4096 2009-05-12 08:43 .pan2
drwxr-xr-x   2 root root       4096 2009-06-05 13:28 passwdgroupbackup
drwxr-xr-x   2 mike root       4096 2009-01-16 13:00 Photos
drwxr-xr-x  21 mike root       4096 2009-06-08 11:27 Pictures
drwxr-xr-x   4 mike mike       4096 2009-05-29 20:12 PipeWalker-0.2.1
drwxr-xr-x   2 mike mike       4096 2009-04-22 10:39 .predict
-rw-r--r--   1 mike mike         37 2009-05-28 14:06 .printer-groups.xml
-rwxr-xr-x   1 mike mike        597 2009-04-27 20:55 .profile
-rw-r--r--   1 mike mike        586 2009-01-16 11:37 .profile~
-rw-r--r--   1 mike mike     111304 2009-05-22 03:25 prox
-rw-r--r--   1 mike mike     111296 2009-05-22 02:33 prox~
drwx------   2 mike mike       4096 2009-06-08 09:10 .pulse
-rwxr-xr-x   1 mike mike        256 2009-01-16 11:37 .pulse-cookie
drwxr-xr-x   5 mike root       4096 2009-06-06 17:44 .purple
drwxr-xr-x  10 mike mike       4096 2005-06-13 20:26 pycrypto-2.0.1
drwxr-xr-x   2 mike mike       4096 2009-03-26 14:02 .qt
-rwxr-xr-x   1 mike mike      12016 2009-05-24 01:03 .recently-used
-rw-------   1 mike mike    3149370 2009-06-08 20:38 .recently-used.xbel
-rw-r--r--   1 mike mike    4833280 2009-06-05 15:25 .recently-used.xbel.7LCUUU
-rw-r--r--   1 mike mike    4828832 2009-06-04 17:56 .recently-used.xbel.HUBSUU
-rw-r--r--   1 mike mike    4798914 2009-05-29 23:31 .recently-used.xbel.MG3SUU
-rw-r--r--   1 mike mike    4807939 2009-05-30 16:55 .recently-used.xbel.NNQXUU
-rw-r--r--   1 mike mike    4798914 2009-05-29 23:31 .recently-used.xbel.WCWXUU
-rwxr-xr-x   1 mike mike        237 2009-06-02 23:07 .registry
drwxr-xr-x   3 mike root       4096 2009-01-16 13:01 .sane
-rw-r--r--   1 mike mike       2030 2009-05-28 08:16 sarah.html~
-rwxr-xr-x   1 mike mike        384 2009-03-03 20:40 .scummvmrc
-rw-------   1 mike mike          0 2009-06-04 19:21 Sent
-rw-r--r--   1 mike mike       3049 2009-02-05 22:36 servers
drwxr-xr-x   2 mike root       4096 2009-01-16 11:37 ShisenSho
-rw-r--r--   1 mike mike         48 2009-06-01 16:33 snap
drwxr-xr-x   2 mike mike       4096 2009-02-02 05:17 .spumux
drwxr-xr-x   2 mike mike       4096 2009-01-16 13:00 .ssh
-rwxr-xr-x   1 mike mike      72919 2009-01-16 11:37 state tax number.pdf
drwxr-xr-x   3 mike mike       4096 2009-04-25 20:32 .subversion
-rw-r--r--   1 mike mike       1730 2009-05-27 22:22 sudo apt-get install gnome-desktop
-rwxr-xr-x   1 mike mike          0 2009-01-16 13:00 .sudo_as_admin_successful
drwxr-xr-x   4 mike root       4096 2009-01-16 13:00 .sudoku
drwxr-xr-x   2 mike mike       4096 2009-01-16 11:38 Templates
drwxr-xr-x   2 mike mike       4096 2009-01-16 11:37 .themes
drwx------   5 mike mike       4096 2009-04-18 16:16 .thumbnails
drwxr-xr-x   4 mike root       4096 2009-01-16 11:37 .tomboy
-rwxr-xr-x   1 mike mike       5389 2009-01-16 11:38 .tomboy.log
-rwxr-xr-x   1 mike mike       2053 2009-01-16 11:37 translog.20080915140641.log
drwx------   2 mike mike       4096 2009-05-11 09:28 .TrueCrypt
-rw-------   1 mike mike          5 2009-06-08 09:21 .TrueCrypt-lock-mike
drwxrwxr-x  26 mike mike       4096 2007-07-31 15:49 tutorial
drwxr-xr-x   2 mike root       4096 2009-05-27 23:32 .update-manager-core
drwxr-xr-x   2 mike mike       4096 2009-05-28 00:09 .update-notifier
-rw-r--r--   1 mike mike   24962916 2009-06-01 20:09 vic.rar
drwxr-xr-x   3 mike root       4096 2009-06-01 10:02 Videos
-rwx------   1 mike mike       1070 2009-05-21 23:24 vip
drwxr-xr-x   3 mike root       4096 2009-05-28 15:42 .vlc
drwxr-xr-x   2 mike mike       4096 2009-05-30 20:52 .wapi
drwxr-xr-x   4 mike root       4096 2009-05-31 08:14 .wine
-rw-------   1 mike mike        170 2009-06-08 09:10 .Xauthority
drwx------   3 mike mike       4096 2009-06-07 21:42 .xchat2
drwxr-xr-x   2 mike root       4096 2009-01-16 11:37 .xine
-rw-r--r--   1 mike mike        146 2009-05-08 10:06 .xscreensaver-getimage.cache
-rw-r--r--   1 mike mike      29422 2009-06-08 20:39 .xsession-errors
drwx------   3 mike mike       4096 2009-06-06 18:19 .yahoorc
drwxr-xr-x   2 mike mike       4096 2009-05-01 19:56 .yed3
-rw-r--r--   1 mike mike  125109540 2009-05-30 22:32 YMP.rar

```
I can't figure out any pattern to which have mike as group and which have root as group. I do notice that none have write permission for group or other.

I'm afraid I don't know any more to do with this. Maybe someone else will see this who can help more.

---

### Post by lariosa42 on 2009-06-09
Thank you so much!!

I was able to go through my /home directory and change many of the permissions back to what they should have been based on your /home directory.  Things are working MUCH better now (although not quite back to normal, my desktop themes are not recognized, but not big deal).  I'll keep tinkering.  Thank you for everything!

---

### Post by michy99 on 2009-06-09
I'm glad you got some things working anyway. I am curious about how you backed up your files and restored them. Also, do you still have the backup? If so, are the permissions messed up there as well?

---

