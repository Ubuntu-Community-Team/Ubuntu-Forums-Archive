---
title: "My Hard Drive space is rapidly disappearing!"
date: 2008-12-04
forum: General Help
---

### Post by utherpendragonfly on 2008-12-04
A couple of days ago I noticed in my home folder it showed my available HD space as 425 GB. My HD is supposed to be 750 GB, but only shows in system monitor as 682 GB.  
Then yesterday it showed I have 385 GB free space, and right now it says 337 GB free space!
I opened the disk usage analyser just now and scanned my file system (which would include all files, right?) and it shows a total of 73.1 GB. Now if my HD is 682 GB with 309.5 used and 372.5 available, I can't figure out what's using the other 200+ GB.
Are there package files or log files that are somehow multiplying to fill up all that space? I don't know what to do, but at this rate in a week or so I'll have no space left!
I'm attaching this screenshot. Can anyone give me any advice?

---

### Post by 11hjpphty76lkjj on 2008-12-04
It looks like you have a lot of usage in your home directory. Try running:

ls -la ~/

To try and figure out in what directory the space is going..

---

### Post by unutbu on 2008-12-04
Open a terminal and type

```
gksu baobab
```

This will run Disk Usage Analyzer as root. Doing so will allow you to see files that are not readable as a normal user. The Hard Drive space it reports will be different too.

Alternatively, if you want Applications>Accessories>Disk Usage Analyzer to work properly, then go to System>Pref>Main Menu, navigate to Disk Usage Analyzer, click Properties, and edit the Command by adding "gksu" in front of the command (baobab).

You might also be able to recoup space by emptying your trash:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by utherpendragonfly on 2008-12-04
Ok, I ran gksu baobab and got this:

davey@davey-desktop:~$ gksu baobab

** (baobab:13552): WARNING **: error in dir /home/steph: Error stating file '/home/steph/.gvfs': Permission denied

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

...also there's some weird stuff going on in var with backup. Please see new attachment.(Do I need to reinstall Ubuntu?)

---

### Post by utherpendragonfly on 2008-12-04
I also did this:

davey@davey-desktop:~$ ls -la ~/
total 331444
drwxr-xr-x 97 davey davey      4096 2008-12-04 22:04 .
drwxr-xr-x  4 root  root       4096 2008-11-29 13:38 ..
drwx------  2 davey davey      4096 2008-12-03 11:50 .AbiSuite
drwx------  3 davey davey      4096 2008-10-21 22:16 .adobe
-rw-r--r--  1 davey davey      7136 2008-11-18 22:16 Alloy-1.1.tar.gz
drwxr-xr-x  2 davey davey      4096 2008-11-17 13:37 .aptoncd
-rw-r--r--  1 davey davey 334385152 2008-11-17 13:41 aptoncd-20081117-CD1.iso
drwxrwxrwx  3 davey davey      4096 2008-10-22 08:41 Arthur Fiona Website
-rw-------  1 davey davey      2413 2008-12-04 21:54 .bash_history
-rw-r--r--  1 davey davey       220 2008-10-21 11:01 .bash_logout
-rw-r--r--  1 davey davey      3115 2008-10-21 11:01 .bashrc
drwxr-xr-x  2 davey davey      4096 2008-10-22 08:41 Battlestar Galactica
drwxr-xr-x  9 davey davey      4096 2008-11-14 11:00 .cache
-rw-r--r--  1 davey davey       240 2008-11-18 16:14 .chromium
-rw-r--r--  1 davey davey      3800 2008-11-18 16:14 .chromium-score
-rw-r--r--  1 davey davey    149843 2008-11-17 09:56 colorizeme-shiki-0.2.tar.gz
drwx------  3 davey davey      4096 2008-10-21 23:49 .compiz
drwxr-xr-x 17 davey davey      4096 2008-12-04 07:33 .config
drwxrwxrwx  7 davey davey      4096 2008-10-22 08:41 Dave's Writing
drwx------  3 davey davey      4096 2008-10-21 11:06 .dbus
drwxr-xr-x  2 davey davey      4096 2008-12-04 22:04 Desktop
-rw-r--r--  1 davey davey        51 2008-11-11 16:21 .devede
-rw-------  1 davey davey        28 2008-12-04 07:33 .dmrc
drwxr-xr-x  6 davey davey      4096 2008-12-03 09:41 Documents
drwxr-xr-x  2 davey davey      4096 2008-12-04 19:20 DOWNLOADS
drwxrwxrwx  9 davey davey      4096 2008-10-22 08:42 Dragonflyarts- Business
drwxrwxrwx 10 davey davey      4096 2008-10-22 08:41 Dragonflyarts.com
drwxr-xr-x  5 davey davey      4096 2008-11-29 10:20 .dvdcss
drwxr-xr-x  2 davey davey      4096 2008-11-11 17:01 .dvdrip
drwxr-xr-x  3 davey davey      4096 2008-11-29 10:28 dvdrip-data
drwxr-xr-x  4 davey davey      4096 2008-11-11 17:01 .dvdrip-master
-rw-r--r--  1 davey davey     25772 2008-11-11 17:21 .dvdriprc
drwxr-xr-x  3 davey davey      4096 2008-10-22 08:42 eBooks
drwxr-xr-x  3 davey davey      4096 2008-11-23 20:00 .elisa-0.5
drwxr-xr-x  4 davey davey      4096 2008-11-03 23:29 .emerald
-rw-------  1 davey davey        16 2008-10-21 11:06 .esd_auth
drwxr-xr-x  2 davey davey      4096 2008-12-02 11:17 .etracer
-rw-r--r--  1 davey davey       292 2008-10-26 22:22 .fbhighlevelshistory
-rw-r--r--  1 davey davey       194 2008-10-26 22:22 .fbhighscores
drwxr-xr-x  2 davey davey      4096 2008-10-26 22:18 .fblevels
-rw-r--r--  1 davey davey      1196 2008-10-26 22:18 .fbrc
drwxr-xr-x  2 davey davey      4096 2008-11-28 12:12 .fontconfig
drwxr-xr-x  2 davey davey      4096 2008-10-30 20:18 .fonts
drwxr-xr-x  3 davey davey      4096 2008-12-01 12:37 .fretsonfire
drwxr-xr-x  5 davey davey      4096 2008-10-22 08:42 Gardening
drwx------  5 davey davey      4096 2008-12-04 18:06 .gconf
drwx------  2 davey davey      4096 2008-12-04 22:05 .gconfd
drwx------  4 davey davey      4096 2008-10-31 10:51 .gegl-0.0
drwxr-xr-x 22 davey davey      4096 2008-11-27 23:02 .gimp-2.6
-rw-r-----  1 davey davey         0 2008-12-04 21:51 .gksu.lock
drwx------ 15 davey davey      4096 2008-12-01 12:36 .gnome2
drwx------  2 davey davey      4096 2008-10-21 11:06 .gnome2_private
drwx------  2 davey davey      4096 2008-10-21 11:06 .gnupg
drwxr-xr-x  4 davey davey      4096 2008-11-02 22:29 GNUstep
drwxr-xr-x 31 davey davey      4096 2008-10-29 15:31 GRAPHICS
drwxr-xr-x  2 davey davey      4096 2008-11-13 22:06 .gstreamer-0.10
-rw-r--r--  1 davey davey       281 2008-12-04 18:27 .gtk-bookmarks
-rw-r--r--  1 davey davey       161 2008-11-20 22:02 .gtkrc-2.0
-rw-r--r--  1 davey davey       161 2008-11-20 22:02 .gtkrc.bak
dr-x------  2 davey davey         0 2008-12-04 07:33 .gvfs
drwxr-xr-x  2 davey davey      4096 2008-11-08 19:47 .helix
drwxr-xr-x  2 davey davey      4096 2008-11-17 13:33 .hubackup-data
-rw-------  1 davey davey     10559 2008-12-04 07:33 .ICEauthority
-rw-------  1 davey davey      9523 2008-11-29 13:29 .ICEauthority.before_restore_2008-11-29_13.38.41.765710
-rw-r--r--  1 davey davey    624328 2008-11-18 22:24 ICON-BlankOn.tar.gz
drwxr-xr-x 17 davey davey      4096 2008-11-18 22:53 .icons
-rw-r--r--  1 davey davey    521236 2008-11-18 22:25 ICON-Snow-Apple.tar.gz
-rw-r--r--  1 davey davey   1471962 2008-11-18 22:42 ICON-UnofficialTango.tar.bz2
drwxrwxrwx  2 davey davey      4096 2008-11-24 13:10 Important Info
drwxr-x---  7 davey davey      4096 2008-10-29 12:40 .inkscape
drwxr-xr-x  3 davey davey      4096 2008-11-13 21:37 .java
drwx------  3 davey davey      4096 2008-10-24 15:35 .kde
drwxr-xr-x  2 davey davey      4096 2008-11-12 12:58 .lemonrip
drwx------  4 davey davey      4096 2008-11-03 09:42 .liferea_1.4
drwx------  3 davey davey      4096 2008-10-21 11:06 .local
drwx------  3 davey davey      4096 2008-10-21 22:16 .macromedia
-rw-r--r--  1 davey davey      3146 2008-11-08 19:49 .mailcap
-rw-r--r--  1 davey davey     31530 2008-11-18 22:13 MCity-Black.tar.gz
-rw-r--r--  1 davey davey      8176 2008-11-18 22:15 MCity-Chiro.tar.gz
-rw-r--r--  1 davey davey      3932 2008-11-18 22:12 MCity-Clearlooks2.tar.gz
-rw-r--r--  1 davey davey      5176 2008-11-18 22:13 MCity-ClearlooksBlend.tar.bz2
-rw-r--r--  1 davey davey     14828 2008-11-18 22:09 MCity-DarkX-2.tar.gz
-rw-r--r--  1 davey davey     16179 2008-11-18 22:14 MCity-QuietHuman.tar.gz
-rw-r--r--  1 davey davey     15258 2008-11-18 22:12 MCity-Shiny.tar.gz
-rw-r--r--  1 davey davey      7107 2008-11-18 22:11 MCity-Slate.tar.gz
drwxr-xr-x  3 davey davey      4096 2008-11-09 15:55 .mcop
-rw-------  1 davey davey        31 2008-11-09 15:55 .mcoprc
drwx------  4 davey davey      4096 2008-10-21 22:56 .mozilla
drwx------  3 davey davey      4096 2008-10-21 22:56 .mozilla-thunderbird
drwxr-xr-x  2 davey davey      4096 2008-10-29 23:01 .mplayer
drwxr-xr-x  2 davey davey      4096 2008-10-12 01:35 MurrineSVN
drwxr-xr-x  5 davey davey      4096 2008-11-14 14:57 Music
drwxr-xr-x  5 davey davey      4096 2008-10-22 08:44 My Artwork
drwxr-xr-x  6 davey davey      4096 2008-12-01 12:06 My GCompris
drwxr-xr-x  3 davey davey      4096 2008-11-28 11:13 .mypaint
-rw-r--r--  1 davey davey    210576 2008-11-18 22:26 Nature.tar.bz2
drwxr-xr-x  3 davey davey      4096 2008-11-30 09:33 .nautilus
drwxr-xr-x  2 davey davey      4096 2008-12-02 10:56 .neverball
-rw-r--r--  1 davey davey      1069 2008-11-10 21:23 .nvidia-settings-rc
drwxr-xr-x  3 davey davey      4096 2008-11-07 23:26 .openoffice.org
drwx------  3 davey davey      4096 2008-11-05 15:57 .openoffice.org2
drwxr-xr-x  2 davey davey      4096 2008-10-22 08:45 Parenting
drwxr-xr-x  3 davey davey      4096 2008-11-04 08:53 PDFs
drwxr-xr-x  4 davey davey      4096 2008-11-09 18:32 .picasa
drwxr-xr-x  4 davey davey      4096 2008-10-23 21:21 Pictures
drwxr-x--- 10 davey davey      4096 2008-11-28 19:06 .pingus
drwxr-xr-x 22 davey davey     20480 2008-10-22 08:44 Politics
-rw-r--r--  1 davey davey       675 2008-10-21 11:01 .profile
drwxr-xr-x  2 davey davey      4096 2008-10-21 11:06 Public
drwxr-xr-x  2 davey davey      4096 2008-11-29 13:38 .pulse
-rw-------  1 davey davey       256 2008-10-21 11:06 .pulse-cookie
drwx------  5 davey davey      4096 2008-11-30 22:02 .purple
drwxr-xr-x  3 davey davey      4096 2008-11-03 09:46 .pyroom
drwxr-xr-x  2 davey davey      4096 2008-10-28 18:37 .qt
-rw-------  1 davey davey      1387 2008-11-19 21:54 .recently-used
-rw-------  1 davey davey      8840 2008-12-04 22:04 .recently-used.xbel
drwxrwxrwx  8 davey davey     12288 2008-11-24 17:29 Recipes
-rw-r--r--  1 davey davey       237 2008-11-24 08:41 .registry
drwxrwx---  3 davey davey      4096 2008-11-08 16:01 .sane
drwxr-xr-x  4 davey davey      4096 2008-10-31 14:12 .scribus
-rw-r--r--  1 davey davey    899805 2008-11-28 12:43 sketch001.png
drwxr-xr-x  6 davey davey      4096 2003-01-29 16:43 Snow-Apple
drwx------  4 davey davey      4096 2008-11-14 23:40 .songbird2
drwxr-xr-x  2 davey davey      4096 2008-11-11 16:16 .spumux
-rw-r--r--  1 davey davey         0 2008-10-21 11:10 .sudo_as_admin_successful
drwxr-xr-x  2 davey davey      4096 2008-10-21 11:06 Templates
drwxr-xr-x 36 davey davey      4096 2008-11-19 22:40 .themes
drwx------  5 davey davey      4096 2008-11-23 19:56 .thumbnails
drwxr-xr-x  4 davey davey      4096 2008-10-27 22:28 .tomboy
-rw-r--r--  1 davey davey      4686 2008-12-04 07:33 .tomboy.log
-rw-r--r--  1 davey davey      4800 2008-11-29 13:42 .tomboy.log.before_restore_2008-11-29_13.38.41.765710
-rw-r--r--  1 root  root          0 2008-11-13 21:34 ubuntu-restricted-extras
drwxr-xr-x  4 davey davey      4096 2008-11-28 10:32 .ubuntu-tweak
drwxr-xr-x  2 davey davey      4096 2008-10-21 11:09 .update-manager-core
drwx------  2 davey davey      4096 2008-10-21 11:45 .update-notifier
drwxr-xr-x  2 davey davey      4096 2008-10-22 08:45 URLs
drwxr-xr-x  4 davey davey      4096 2008-10-12 00:39 usr
drwxr-xr-x  5 davey davey      4096 2008-11-12 17:40 Videos
drwxr-xr-x  2 davey davey      4096 2008-12-04 07:33 .wapi
drwxr-xr-x  2 davey davey      4096 2008-11-27 22:57 .xaralx
drwxr-xr-x  2 davey davey      4096 2008-11-27 22:51 .XaraLXFilters
-rw-------  1 davey davey       124 2008-12-04 07:33 .Xauthority
-rw-------  1 davey davey       124 2008-11-29 13:29 .Xauthority.before_restore_2008-11-29_13.38.41.765710
drwxr-xr-x  2 davey davey      4096 2008-11-11 10:25 .xine
drwx------  5 davey davey      4096 2008-12-02 11:18 .xmoto
-rw-r--r--  1 davey davey       129 2008-11-09 15:48 .xscreensaver-getimage.cache
-rw-r--r--  1 davey davey      3439 2008-12-04 22:04 .xsession-errors
-rw-r--r--  1 davey davey     42938 2008-11-29 13:42 .xsession-errors.before_restore_2008-11-29_13.38.41.765710

Can anyone decipher this for me. I'm lost right now!

---

### Post by 11hjpphty76lkjj on 2008-12-04
Looks like the backup is the culprit.  Are you running some backup application? Simple backup perhaps?

---

### Post by utherpendragonfly on 2008-12-05
I had Simple Backup installed, so I just uninstalled it. However the file 'Backup' in my var file is locked. Says I don't have permission to access it. Is there a sudo terminal command I can use to delete those old backup files, and what would you recommend I use to do backups. 
I also have Home User Backup installed, and I want to get an external HD soon to backup to. Until a couple months ago I've always used a Mac and had a great GUI app called Super Duper that automatically made a bootable clone of my system every week, only copying files that had changed since previous backup. I don't suppose there's anything that easy to use for Linux, is there?
Thanks for the help.

---

### Post by unutbu on 2008-12-05
```
sudo rm -rf /var/backup/

```
This will delete the entire /var/backup directory. 

Alternatively,
```

gksu nautilus
```

This will give you a nautilus window with root powers. 

For backing up data (such as a home directory),
```

rsync -a /home/user/ /home/user_20081205/
```

This will make a complete copy of /home/user/ and place it at /home/user_20081205/.

For backing up a whole partition, you could use PartImage: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page). Here are two guides on how to use it: 

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

For backing up a whole disk drive (so you could make a "bootable clone" of your system) you could use Clonezilla: [http://www.clonezilla.org/](http://www.clonezilla.org/).

---

### Post by utherpendragonfly on 2008-12-05
I used 'sudo rm -rf /var/backup/' and it worked great! I now have 533 GB free space. Thank you! I also found some web pages on the ubuntu community site with lots of useful terminal commands. I used to be scared to use terminal in OSX, but it certainly comes in handy. I also checked out documentation for Simple Backup, and I must have had the settings wrong (about only copying files that had changed). 
Thanks for the other recommendations, too!

---

