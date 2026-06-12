---
title: "call of duty black ops couldn't write a file; the hard drive is probably full"
date: 2013-12-31
forum: Gaming &amp; Leisure
---

### Post by lord.coetzee on 2013-12-31
Hi, I recently installed ubuntu and found that wine should install .exe programs easily. Well I installed call of duty and warcraft frozen throne with wine version 1.7.8, steam installed and opens perfectly atm, but when I try to open either one of the games I get an error message that my hard drive is full,, though it should have over 150 GB of free space, which is more than enough, I am running ubuntu 12.04 as it should be the most stable. Could anyone plz help, I have googled my self to hell and back and can't find a relavant solution to this. I didn't partition my drive and ubuntu is my main OS atm.

---

### Post by dannyboy79 on 2014-01-01
does this help? [http://ubuntuforums.org/showthread.php?t=179565](http://ubuntuforums.org/showthread.php?t=179565)

---

### Post by lord.coetzee on 2014-01-07
[COLOR=#000000]*/home/intangir/.wine/drive_z/home/intangir -> /home/intangir*[/COLOR]

[COLOR=#000000]*then i changed the Z path in winecfg from / to /home/intangir/.wine/drive_z/home/intangir*[/COLOR]

[COLOR=#000000][I]now it shows the size as being my home directory

so I type into console    .....;   /home/intangir/.wine/drive_z/home/intangir -> /home/intangir

then I change my H: path in wine.cfg to /home/intangir/.wine/drive_z/home/intangir    ,,,, and it should then start game up ?



[/I][/COLOR]

---

### Post by lord.coetzee on 2014-01-09
the link doesn't give a solution,, so no its not help full at all, thnx.

---

### Post by dannyboy79 on 2014-01-10
i don't use wine so I can try to help just by the simple fact of my linux knowledge. first, let's see your hard drives and how much space you're working with. first to see your hard drives and their partitions run this command, it will parse your harddrives and show me each partition table
```
sudo fdisk -l
```
next we need to figure out what partition wine is using as it's "c:/" drive to make sure you have the correct ownership and permissions. if you did a default install, ```
winecfg
``` should have made a .wine folder within your home partition. let's see what your home partition looks like, issue this in a terminal, it will show me all the files and folders in your home directory.
```
ls -la ~/
```

---

### Post by psnel on 2014-01-10
> **lord.coetzee said:**
> the link doesn't give a solution,, so no its not help full at all, thnx.

Are you sure you followed that solution correctly? The one instruction **dannyboy79** gave:
```
ls -la ~/
```
, is meant to list all files and folders in your home folder and subfolders (shortcut: '~' is same as '/home/lordcoetzee'). I think he means to check if the links that solution talks about actually points to the correct places *on _your_ computer*. For instance you can't directly link anything with */home/intangir* as in the solution... that would be that user's home dir. Your's would be **/home/lordcoetzee**.

If I'm correct, your winecfg setup currently looks like this:
[ATTACH=CONFIG]249356[/ATTACH]

This shows that your Z: is still pointing to your root directory: '/'
The instructions said you must set Z: to (in your case..) */home/lordcoetzee/.wine/drive_z/home/lordcoetzee*. But first:
[LIST]
[*]You'd have to create the folder */home/lordcoetzee/.wine/drive_z/home/*
```
mkdir -p /home/lordcoetzee/.wine/drive_z/home
```

[*]Then inside that folder, create a "sym link" (aka a symbolic link. NB **not** hard link) to your home folder */home/lordcoetzee*
```
ln -s ~ /home/lordcoetzee/.wine/drive_z/home/lordcoetzee
```

[*]Then point wine's Z: to that (symlinked) folder; i.e. in stead of to root /
[/LIST]

Does it make sense?

---

### Post by lord.coetzee on 2014-01-10
lordcoetzee@LordCoetzee:~$ sudo fdisk -l
[sudo] password for lordcoetzee: 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?  1936269394  3772285809   918008208    7  HPFS/NTFS/exFAT
/dev/sda2   ?  1917848077  2462285169   272218546+  73  Unknown
/dev/sda3   ?  1818575915  2362751050   272087568   2b  Unknown
/dev/sda4   ?  2844524554  2844579527       27487   61  SpeedStor


Partition table entries are not in disk order


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001bdd6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   481583103   240790528   83  Linux
/dev/sdb2       481585150   488396799     3405825    5  Extended
/dev/sdb5       481585152   488396799     3405824   82  Linux swap / Solaris
lordcoetzee@LordCoetzee:~$

EVERY THING IS INSTALLED ON THE 250GB DRIVE ,,,

---

### Post by lord.coetzee on 2014-01-10
yes thats what my wine cfg looks like

---

### Post by lord.coetzee on 2014-01-10
lordcoetzee@LordCoetzee:~$ ls -la ~/
total 304
drwxr-xr-x 39 lordcoetzee lordcoetzee  4096 Jan 10 04:34 .
drwxr-xr-x  3 root        root         4096 Dec 26 16:21 ..
drwx------  3 lordcoetzee lordcoetzee  4096 Dec 26 17:13 .adobe
drwxrwxr-x  4 lordcoetzee lordcoetzee  4096 Jan 10 02:34 .audacity-data
-rw-------  1 lordcoetzee lordcoetzee  3146 Jan 10 22:56 .bash_history
-rw-r--r--  1 lordcoetzee lordcoetzee   220 Dec 26 16:21 .bash_logout
-rw-r--r--  1 lordcoetzee lordcoetzee  3486 Dec 26 16:21 .bashrc
drwxrwxr-x  3 lordcoetzee lordcoetzee  4096 Dec 27 14:27 .blender
drwx------ 27 lordcoetzee lordcoetzee  4096 Jan  1 04:11 .cache
drwxrwxr-x  3 lordcoetzee lordcoetzee  4096 Dec 26 16:32 .compiz-1
drwx------ 27 lordcoetzee lordcoetzee  4096 Jan  8 02:20 .config
drwx------  3 lordcoetzee lordcoetzee  4096 Dec 26 16:26 .dbus
drwxr-xr-x  3 lordcoetzee lordcoetzee  4096 Jan 10 22:54 Desktop
-rw-r--r--  1 lordcoetzee lordcoetzee    26 Jan 10 03:34 .dmrc
drwxr-xr-x  5 lordcoetzee lordcoetzee  4096 Dec 31 17:04 Documents
drwxr-xr-x  4 lordcoetzee lordcoetzee  4096 Jan 10 08:13 Downloads
-rw-r--r--  1 lordcoetzee lordcoetzee  8445 Dec 26 16:21 examples.desktop
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Jan  1 14:57 .fontconfig
drwx------  5 lordcoetzee lordcoetzee  4096 Jan 10 03:34 .gconf
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 26 21:13 .gegl-0.0
drwxr-xr-x 22 lordcoetzee lordcoetzee  4096 Jan  1 17:02 .gimp-2.6
-rw-r-----  1 lordcoetzee lordcoetzee     0 Jan  7 16:42 .gksu.lock
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 26 16:26 .gnome2
-rw-------  1 lordcoetzee lordcoetzee     0 Dec 26 16:14 .goutputstream-7CJN8W
-rw-------  1 lordcoetzee lordcoetzee     0 Jan  3 17:13 .goutputstream-AI928W
-rw-------  1 lordcoetzee lordcoetzee     0 Jan  3 14:56 .goutputstream-B51C9W
-rw-------  1 lordcoetzee lordcoetzee     0 Dec 31 02:58 .goutputstream-RF4V8W
drwxrwxr-x  2 lordcoetzee lordcoetzee  4096 Dec 28 12:20 .gstreamer-0.10
-rw-rw-r--  1 lordcoetzee lordcoetzee   167 Jan 10 03:34 .gtk-bookmarks
dr-x------  2 lordcoetzee lordcoetzee     0 Jan 10 03:34 .gvfs
-rw-------  1 lordcoetzee lordcoetzee 22674 Jan 10 03:34 .ICEauthority
drwxrwxr-x  2 lordcoetzee lordcoetzee  4096 Jan  7 18:18 .idlerc
drwxr-xr-x  3 lordcoetzee lordcoetzee  4096 Dec 26 16:26 .local
drwx------  3 lordcoetzee lordcoetzee  4096 Dec 26 17:13 .macromedia
drwx------  3 lordcoetzee lordcoetzee  4096 Dec 26 16:26 .mission-control
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 26 16:43 .mozilla
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Dec 26 16:26 Music
drwx------  3 lordcoetzee lordcoetzee  4096 Dec 27 00:50 .nv
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Jan 10 04:45 Pictures
drwx------  3 lordcoetzee lordcoetzee  4096 Jan  1 02:21 .pki
drwxrwxr-x 14 lordcoetzee lordcoetzee  4096 Jan 10 03:57 .PlayOnLinux
lrwxrwxrwx  1 lordcoetzee lordcoetzee    43 Jan 10 02:46 PlayOnLinux's virtual drives -> /home/lordcoetzee/.PlayOnLinux//wineprefix/
drwxr-xr-x 13 lordcoetzee lordcoetzee  4096 Dec 26 23:04 POL-POM-4
-rw-r--r--  1 lordcoetzee lordcoetzee   675 Dec 26 16:21 .profile
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Dec 26 16:26 Public
drwx------  2 lordcoetzee lordcoetzee  4096 Jan  9 14:59 .pulse
-rw-------  1 lordcoetzee lordcoetzee   256 Dec 26 16:26 .pulse-cookie
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 26 23:15 .speech-dispatcher
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Dec 26 16:26 Templates
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 27 16:15 .thumbnails
drwx------  4 lordcoetzee lordcoetzee  4096 Dec 26 15:30 .thunderbird
drwxrwxr-x  2 lordcoetzee lordcoetzee  4096 Dec 26 15:13 Ubuntu One
drwxr-xr-x  2 lordcoetzee lordcoetzee  4096 Dec 26 16:26 Videos
-rw-rw-r--  1 lordcoetzee lordcoetzee     9 Jan 10 03:25 .windows-serial
drwxrwxr-x  4 lordcoetzee lordcoetzee  4096 Jan 10 22:54 .wine
-rw-------  1 lordcoetzee lordcoetzee    56 Jan 10 03:34 .Xauthority
-rw-------  1 lordcoetzee lordcoetzee 57764 Jan 10 22:35 .xsession-errors
-rw-------  1 lordcoetzee lordcoetzee 11016 Jan 10 03:34 .xsession-errors.old
lordcoetzee@LordCoetzee:~$

I installed playonlinux to see if it makes any difference, no it didn't

---

### Post by lord.coetzee on 2014-01-10
I didn't do anything regarding this link [http://ubuntuforums.org/showthread.php?t=179565](http://ubuntuforums.org/showthread.php?t=179565) because it does not indicate what I should do, and I don't want to start typing alot of gibrish and then destroy my pc.

---

### Post by lord.coetzee on 2014-01-10
following psnel's info this is what happened ;;;

lordcoetzee@LordCoetzee:~$ mkdir -p /home/lordcoetzee/.wine/drive_z/home
lordcoetzee@LordCoetzee:~$ ln -s ~ /home/lordcoetzee/.wine/drive_z/home/lordcoetzee
lordcoetzee@LordCoetzee:~$ 

now how do I point the Z drive to the link...   did it even create a link,, looks to me like it didn't do anything

thnx kindly. to both of you for trying to help me with this.

---

### Post by lord.coetzee on 2014-01-10
[IMG]http://i1062.photobucket.com/albums/t482/Lord_Coetzee/Screenshotfrom2014-01-10225442_zps4061bd79.png?t=1389388334[/IMG]  winecfg

---

### Post by psnel on 2014-01-13
> **lord.coetzee said:**
> I didn't do anything regarding this link [http://ubuntuforums.org/showthread.php?t=179565](http://ubuntuforums.org/showthread.php?t=179565) because it does not indicate what I should do, and I don't want to start typing alot of gibrish and then destroy my pc.

Yes it does indicate. Read carefully. You even quoted it previously. And I also re-stated and explained the instructions.

Read.. Think.. Do.

---

### Post by lord.coetzee on 2014-01-13
No, it does not indicate how to make a link ,, or how to set the Z drive,, and if you opened your eyes; you would've seen that I did follow your steps ,, but it was useless as usual, and didn't do anything. So its not necessary to insult me by telling me I can't read think or do ... if you don't want to help then don't. I can also tell you you can make $1000 000 in forex, and just leave you hanging ,, and when you lose your money,, then I can tell you your a stupid idiot that can't read think or do.  

[COLOR=#000000]"lordcoetzee@LordCoetzee:~$ mkdir -p /home/lordcoetzee/.wine/drive_z/home[/COLOR]
[COLOR=#000000]lordcoetzee@LordCoetzee:~$ ln -s ~ /home/lordcoetzee/.wine/drive_z/home/lordcoetzee[/COLOR]
[COLOR=#000000]lordcoetzee@LordCoetzee:~$ [/COLOR]

[COLOR=#000000]now how do I point the Z drive to the link... did it even create a link,, looks to me like it didn't do anything[/COLOR]

[COLOR=#000000]thnx kindly. to both of you for trying to help me with this."

SO WHERES THE INSTRUCTIONS ??[/COLOR][IMG]https://www.facebook.com/photo.php?fbid=680037458705589&set=a.302775859765086.68974.302772516432087&type=1[/IMG][COLOR=#000000]

[/COLOR]

---

### Post by psnel on 2014-01-13
We use command line on the forum because it's easier to copy/paste and not make mistakes. Otherwise i'd have to narrate a long story that's difficult to follow; plus I can't see what's on your screen, so I'd have to make assumptions... they're often wrong.

1. The first command (mkdir) should have created a folder under /home/lordcoetzee/.wine/drive_z/ called 'home'. Feedback is only given when the command FAILS. So it looks like this one succeeded.
2. The second command (ln -s) should have created a symbolic link in that folder, named 'lordcoetzee' (if you browse to that nested home folder and view its properties, you'd see the link target is your home folder, i.e. '~')
To see the results on the command-line do:
```

$ ls -l /home/lordcoetzee/.wine/drive_z/home

```
(list that directory's contents, in 'long' format)

You should see something like this:
```

...
lrwxrwxrwx  1 lordcoetzee lordcoetzee         37 Dec  6  2012 lordcoetzee -> /home/lordcoetzee/
...

```
(i.e. a link to a directory. That is the 'file' that you're mapping to Z: )

3. To map it to Z: in winecfg, click on Z: in wine config's Drive Configuration box (in your screenshot). In the input box where it says "Path:" type, or copy the path to that link we made (/home/lordcoetzee/.wine/drive_z/home/lordcoetzee)
NOTE: just make sure that path is in fact correct as on your system.

...this should map that link to Z: in stead of '/' (as it shows on your last screenshot).


**TIP: [COLOR="#FF0000"]Getting comfortable with a new OS takes time and patience. If there's something you don't understand, like "what is a symbolic link in linux", then do an internet search for it.[/COLOR]** No offense. Sometimes we have to be told such things.

---

### Post by lord.coetzee on 2014-01-13
[COLOR=#0000ff]Didn't you read my first post ?[/COLOR]   [COLOR=#000000][/COLOR][COLOR=#ff0000] "I have googled my self to hell and back and can't find a relavant solution to this" BUT YOU AUTOMATICALLY ASSUME I DID NOTHING.[/COLOR][COLOR=#000000]

[SIZE=3]no one just makes post like this for the fun,,, any idiot would search google first.[/SIZE]

[/COLOR]but ok I got this ,, , 

[COLOR=#ff0000]lordcoetzee@LordCoetzee:~$ ls -l /home/lordcoetzee/.wine/drive_z/home[/COLOR]
[COLOR=#ff0000]total 0[/COLOR]
[COLOR=#ff0000]lrwxrwxrwx 1 lordcoetzee lordcoetzee 17 Jan 10 23:04 lordcoetzee -> /home/lordcoetzee[/COLOR]



[COLOR=#ff0000]
[/COLOR]
[COLOR=#000000]my wine cfg z: is now [/COLOR]  ;;;;   [COLOR=#0000ff] /home/lordcoetzee/.wine/drive_z/home[/COLOR]
[COLOR=#000000]
still getting the same error ....   


[/COLOR]

---

### Post by lord.coetzee on 2014-01-13
Well I changed to z drive to c drive but still same error ,,, so mayb intalling mess up,,, so I am going to reinstall it now and see what happens...

ok so I made these links now,, one for Z: and one for C: ,,, how do I undo them ?

---

### Post by lord.coetzee on 2014-01-13
well I reinstalled the game ,, but now i'm stuck with a differrent error,,, don't think the above had any thing to do with it. [IMG]http://s1062.photobucket.com/user/Lord_Coetzee/media/Screenshotfrom2014-01-13231815_zps446bb82d.png.html[/IMG]
[URL="http://s1062.photobucket.com/user/Lord_Coetzee/media/Screenshotfrom2014-01-13231815_zps446bb82d.png.html"]
http://s1062.photobucket.com/user/Lord_Coetzee/media/Screenshotfrom2014-01-13231815_zps446bb82d.png.html[/URL]

so I contacted steam support and hope they come back to me.

---

