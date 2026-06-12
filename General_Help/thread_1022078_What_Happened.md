---
title: "What Happened?"
date: 2008-12-26
forum: General Help
---

### Post by s][re on 2008-12-26
I lost a directory and don't even know how.

I went to my PC this morning to work on a paper for school.  Looked for a directory called "Documents" that I've had on my PC for 6 months now, and all of the sudden it's gone!  WTF happened?  Nothing in the Trash bin, and I did a search for "find / -name Documents" and found nothing.

Any ideas?  Please help.

Thanks in advance.

---

### Post by taurus on 2008-12-26
Is that directory, Documents, in your $HOME?

```
ls -la ~
```

---

### Post by s][re on 2008-12-26
> **taurus said:**
> Is that directory, Documents, in your $HOME?

```
ls -la ~
```
It's not there anymore

---

### Post by s][re on 2008-12-26
Any ideas where it mysteriously disappeared to?

---

### Post by s][re on 2008-12-26
Tried recovering with Foremost and came up blank -- ??

Any advice?  What could have happened?

---

### Post by Monotoko on 2008-12-26
Does anybody else use your computer? (siblings, family, etc) that may have accidently deleted it?

---

### Post by s][re on 2008-12-26
> **Monotoko said:**
> Does anybody else use your computer? (siblings, family, etc) that may have accidently deleted it?
Nope, I'm the only one.  The folder disappeared from one hour to the next.  It has to be somewhere, and I thought for sure I would be able to recover it using Foremost.

I'm trying Photorec now, but it's not finding recent files and it's very "scattered".

---

### Post by scandido on 2008-12-26
This advice is extremely trivial, but perhaps you should look at the command history of your terminal to see if you can find a "mv Documents somewhere" or "rm -r Documents" anywhere. 

Also, you could attempt to search for a file you know to be inside your Documents folder. If the folder somehow got renamed then this might find it. 

Good luck.

---

### Post by s][re on 2008-12-26
> **scandido said:**
> This advice is extremely trivial, but perhaps you should look at the command history of your terminal to see if you can find a "mv Documents somewhere" or "rm -r Documents" anywhere. 

Also, you could attempt to search for a file you know to be inside your Documents folder. If the folder somehow got renamed then this might find it. 

Good luck.
I tried that as well and came up empty.  This is so damn strange.

---

### Post by taurus on 2008-12-26
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la ~
```

---

### Post by s][re on 2008-12-26
> **taurus said:**
> Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la ~
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b77c05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29172   234324058+  83  Linux
/dev/sda2           29173       30401     9871942+   5  Extended
/dev/sda5           29173       30401     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 4005 MB, 4005560320 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf315f315




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=736705d9-e95e-4024-abd3-c73b3c349620 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dcc46307-7054-47ec-ba9c-9c52e6604c35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0





Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  139G   70G  67% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  148K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  428K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-11-generic/volatile




drwx------ 104    4096 2008-12-27 00:42 .

drwxr-xr-x   4    4096 2008-11-13 06:18 ..

drwx------   5    4096 2008-12-06 08:10 .adobe

drwxr-xr-x   2    4096 2008-11-09 10:34 .aptoncd

drwx------   4    4096 2008-12-25 08:15 .aqbanking

drwxr-xr-x   4    4096 2008-11-09 10:57 .audacity-data

drwxr-xr-x   4    4096 2008-11-22 07:27 .avg7

drwxr-xr-x   3    4096 2008-11-30 12:51 .avidemux

-rw-------   1    7081 2008-12-27 00:46 .bash_history

-rw-r--r--   1     220 2008-11-03 20:21 .bash_logout

-rw-r--r--   1    3115 2008-11-03 20:21 .bashrc

drwxr-xr-x   2    4096 2008-11-23 18:22 .bluefish

drwxr-xr-x   8    4096 2008-11-30 19:52 .cache

drwxr-xr-x   4    4096 2008-11-07 21:12 .clamtk

drwxr-xr-x   3    4096 2008-12-21 18:02 .codeblocks

drwx------   3    4096 2008-11-04 21:59 .compiz

drwxr-xr-x  22    4096 2008-12-26 20:25 .config

drwx------   2    4096 2008-11-27 20:06 .cups

drwx------   3    4096 2008-11-03 20:57 .dbus

drwxr-xr-x   3    4096 2008-12-26 16:24 Desktop

-rw-r--r--   1      52 2008-12-21 08:39 .devede

-rw-------   1      28 2008-12-26 20:25 .dmrc

drwxrwxrwx  24    4096 2008-12-26 20:35 Downloads

drwxr-xr-x   2    4096 2008-11-09 14:12 dwhelper

-rw-------   1       0 2008-11-23 18:20 en_US.UTF-8

-rw-------   1      16 2008-11-03 20:57 .esd_auth

drwxr-xr-x   8    4096 2008-11-25 20:03 .evolution

-rw-r--r--   1    1196 2008-11-15 20:37 .fbrc

drwx------   2    4096 2008-11-21 23:35 .filezilla

drwxr-xr-x   2    4096 2008-12-04 21:27 .fontconfig

-rw-r--r--   1     621 2008-11-28 07:32 .fonts.conf

drwxr-xr-x   2    4096 2008-12-27 00:26 foremost

drwxr-xr-x   2    4096 2008-11-04 22:48 .FuriusIsoMount

drwx------   4    4096 2008-12-26 20:25 .gconf

drwx------   2    4096 2008-12-27 00:51 .gconfd

drwx------   5    4096 2008-12-21 19:58 .geany

drwx------   4    4096 2008-11-16 01:58 .gegl-0.0

drwxr-xr-x  22    4096 2008-12-24 22:53 .gimp-2.6

-rw-r-----   1       0 2008-12-26 20:26 .gksu.lock

drwx------   3    4096 2008-11-04 20:05 .gnome

drwx------  18    4096 2008-12-26 20:36 .gnome2

drwx------   2    4096 2008-11-03 20:57 .gnome2_private

drwx------   4    4096 2008-11-05 20:56 .gnucash

drwx------   2    4096 2008-11-30 20:01 .gnupg

drwx------   6    4096 2008-12-24 21:28 .googleearth

drwxr-xr-x   9    4096 2008-11-04 20:05 google-earth

drwxr-xr-x   3    4096 2008-11-17 20:17 .gscrot

drwxr-xr-x   2    4096 2008-11-09 11:58 .gstreamer-0.10

-rw-r--r--   1     175 2008-12-26 20:31 .gtk-bookmarks

-rw-r--r--   1     237 2008-11-11 17:38 .gtk-custom-papers

drwxr-x---   3    4096 2008-12-22 21:00 .gtk-gnutella

drwxr-xr-x   5    4096 2008-11-08 10:54 gtk-gnutella-downloads

-rw-r--r--   1     948 2008-11-18 21:44 .gtk-recordmydesktop

dr-x------   2       0 2008-12-26 20:25 .gvfs

drwxr-xr-x   2    4096 2008-11-18 21:44 .helix

drwx------   2    4096 2008-11-11 09:07 .homebank

drwxr-----   2    4096 2008-12-20 13:49 .hplip

-rw-r--r--   1      34 2008-12-07 04:40 .httrack.ini

-rw-------   1    5620 2008-12-26 20:25 .ICEauthority

drwxr-xr-x   3    4096 2008-11-09 11:23 .icons

-rw-r--r--   1    4161 2008-12-26 15:58 .installationinformation

-rw-r--r--   1    1074 2008-11-25 21:49 <invalid path>

-rw-r--r--   1     139 2008-11-25 21:50 <invalid path>.layout

-rw-r--r-x   1      23 2008-11-30 13:20 .jackdrc

drwxr-xr-x   3    4096 2008-11-07 06:26 .java

drwxr-xr-x   2    4096 2008-11-05 20:02 .kchmviewer

drwx------   3    4096 2008-11-27 17:35 .kde

drwx------   2    4096 2008-11-30 12:52 .kino-history

-rw-r--r--   1    2966 2008-11-30 12:51 .kinorc

-rw-r--r--   1    2489 2008-11-30 13:22 .lives

drwx------   2    4096 2008-11-30 13:20 .lives-dir

drwx------   3    4096 2008-12-26 16:00 .local

drwx------   3    4096 2008-11-04 20:05 .loki

drwx------   3    4096 2008-11-04 05:47 .macromedia

-rw-r--r--   1    3146 2008-11-22 07:50 .mailcap

drwxr-xr-x   3    4096 2008-11-05 20:55 .mcop

-rw-------   1      31 2008-12-25 08:14 .mcoprc

drwxr-xr-x   2    4096 2008-11-04 21:00 media

drwxr-xr-x   5    4096 2008-12-21 22:38 .miro


drwx------   5    4096 2008-12-13 23:05 .mozilla

drwx------   4    4096 2008-11-08 16:19 .mozilla.backup

drwx------   3    4096 2008-11-09 14:45 .mozilla-thunderbird

drwxr-xr-x   2    4096 2008-11-30 08:39 .mplayer

drwxr-xr-x   2   45056 2008-12-26 23:58 Music

drwxr-xr-x   3    4096 2008-12-26 18:19 .nautilus

-rw-------   1    9673 2008-11-15 10:10 .nessusrc

-rw-r--r--   1      51 2008-11-15 10:02 .nessusrc.cert

drwxr-xr-x   3    4096 2008-11-10 21:42 .netbeans

drwxr-xr-x   3    4096 2008-11-10 21:42 .netbeans-registration

-rw-------   1     212 2008-11-15 20:31 .notifier.conf

-rw-r--r--   1    1125 2008-11-27 17:21 .nvidia-settings-rc

drwxr-xr-x   3    4096 2008-11-15 19:01 .openoffice.org

drwx------   3    4096 2008-11-15 18:55 .openoffice.org2

-rw-r--r--   1  419715 2008-12-27 00:29 photorec.ses

drwxr-xr-x   4    4096 2008-11-27 20:29 .picasa

drwxr-xr-x  30   12288 2008-12-22 20:09 Pictures

drwxr-xr-x  10    4096 2008-11-29 12:27 .PlayOnLinux

-rw-r--r--   1     675 2008-11-03 20:21 .profile

drwxr-xr-x   3    4096 2008-12-26 16:24 Programming

drwxr-xr-x   2    4096 2008-11-03 20:57 Public

drwxr-xr-x   2    4096 2008-12-04 09:44 .pulse

-rw-------   1     256 2008-11-03 20:57 .pulse-cookie

drwx------   6    4096 2008-12-26 23:43 .purple

drwxr-xr-x   3    4096 2008-11-09 10:28 .pybackpack

drwxr-xr-x   2    4096 2008-11-20 04:22 .qt

drwxr-xr-x   2    4096 2008-11-05 17:08 QuickStart

-rw-------   1   51603 2008-12-26 10:32 .recently-used

-rw-------   1    8580 2008-12-26 20:37 .recently-used.xbel

drwxrwx---   3    4096 2008-11-11 20:02 .sane

drwx------   4    4096 2008-11-10 08:27 .screem

drwxr-xr-x   2    4096 2008-12-12 05:45 .serpentine

drwxr-xr-x   3    4096 2008-12-25 20:37 .smplayer

drwxr-xr-x   2    4096 2008-11-09 16:33 .spumux

drwx------   2    4096 2008-11-17 20:15 .ssh

drwxr-xr-x   3    4096 2008-11-09 13:18 .streamtuner

drwxr-xr-x   3    4096 2008-11-10 21:42 .subversion

-rw-r--r--   1       0 2008-11-03 20:58 .sudo_as_admin_successful

drwxr-xr--   3    4096 2008-12-27 00:42 -T

drwxr-xr-x   2    4096 2008-11-03 20:57 Templates

drwxr-xr-x   7    4096 2008-11-09 11:24 .themes

drwx------   5    4096 2008-11-08 15:45 .thumbnails

drwxr-xr-x   4    4096 2008-12-13 08:05 .ubuntu-tweak

drwxr-xr-x   2    4096 2008-11-03 21:15 .update-manager-core

drwx------   2    4096 2008-11-08 08:50 .update-notifier

drwxr-xr-x   3    4096 2008-12-18 21:15 .usp

drwxr-xr-x   2    4096 2008-12-26 16:24 Videos

drwxr-xr-x   4    4096 2008-11-15 19:27 .VirtualBox

drwx------   2    4096 2008-11-15 20:31 .w3m

drwxr-xr-x   3    4096 2008-11-21 21:47 .wajig

drwxr-xr-x   2    4096 2008-11-27 20:03 .wapi

drwxr-xr-x   8    4096 2008-12-07 04:40 websites

drwxr-xr-x   4    4096 2008-11-29 12:33 .wine

-rw-------   1     120 2008-12-26 20:25 .Xauthority

drwxr-xr-x   2    4096 2008-12-21 22:38 .xine

-rw-r--r--   1    9108 2008-12-27 00:38 .xsession-errors

---

### Post by taurus on 2008-12-26
You're sure you didn't move or save it to your thumbdrive, 4GB?

---

### Post by mempman on 2008-12-26
try the following:

find / -iname "*document*"

---

### Post by s][re on 2008-12-27
> **taurus said:**
> You're sure you didn't move or save it to your thumbdrive, 4GB?

Nope, checked there as well.

---

### Post by s][re on 2008-12-27
> **mempman said:**
> try the following:

find / -iname "*document*"

It found a lot of documents, but none that were in the Documents folder.

This is mind-boggling. :confused:

---

### Post by ju2wheels on 2008-12-27
Check the .openoffice.org and .openoffice.org2 folders and see if OpenOffice may have saved a temporary copy in there, the one that it backs up every 10 minutes as you work. Im not sure if thats where they are kept or not but it should have put those backups somewhere in your home directory.

---

### Post by s][re on 2008-12-27
> **ju2wheels said:**
> Check the .openoffice.org and .openoffice.org2 folders and see if OpenOffice may have saved a temporary copy in there, the one that it backs up every 10 minutes as you work. Im not sure if thats where they are kept or not but it should have put those backups somewhere in your home directory.

I tried looking for any *.odt extension and found nothing related.  Unfortunately, the last backup I have is from 3 weeks ago. :(

I had a bunch of docs & pics in that directory since the last backup.

---

