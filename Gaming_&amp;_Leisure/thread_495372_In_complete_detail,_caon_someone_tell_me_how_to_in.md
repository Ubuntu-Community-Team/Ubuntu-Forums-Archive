---
title: "In complete detail, caon someone tell me how to install SW:Empire at War?"
date: 2007-07-07
forum: Gaming &amp; Leisure
---

### Post by ~~Tito~~ on 2007-07-07
With Wine?
Please, on winehq it barley gives us noobs a description at all.

---

### Post by ubuntu.daemon on 2007-07-07
lol ok in winecfg, you need to map a drive to wherever you are going to mount the cd to.  Then then go into the directory you just mounted
```
user@home:/media/cdrom$ wine setup.exe
```  and then configure whatever options you need in winecfg, then do the rest as they say, the dll im guessing you find online or maybe in the wine directory

lemee know otherwise:popcorn:

---

### Post by ~~Tito~~ on 2007-07-08
ok so

tito@home:/media/cdrom0/ wine LaunchEAW.exe
?

---

### Post by ~~Tito~~ on 2007-07-08
OH this is what it says

tito@TITOS-LAPTOP:~$ cd /media/cdrom0
tito@TITOS-LAPTOP:/media/cdrom0$ wine LaunchEAW.exe
wine: could not load L"E:\\LaunchEAW.exe": Bad EXE format for 
tito@TITOS-LAPTOP:/media/cdrom0$

---

### Post by ubuntu.daemon on 2007-07-08
Did you set your winecfg to windows XP??  did you link a letter drive to your /media/cdrom0?  mount your cdrom and show me whats in it.
```
user@home: ls -al
```
Did you ever install wine....?
I have version 0.9.33   u'll need to  have to enabled universe and multiverse
[IMG]http://i93.photobucket.com/albums/l80/kappakupo/ubuntu/winky.png[/IMG]
/media/iso is what i mount my iso'd cd's too 
[IMG]http://i93.photobucket.com/albums/l80/kappakupo/ubuntu/winky1.png[/IMG]

---

### Post by ~~Tito~~ on 2007-07-08
tito@TITOS-LAPTOP:~$ ls -al
total 452
drwxr-xr-x 42 tito tito   4096 2007-07-07 22:32 .
drwxr-xr-x  5 root root   4096 2007-07-07 00:41 ..
drwx------  8 tito tito   4096 2007-07-06 23:25 .amsn
drwx------  2 tito tito   4096 2007-07-06 23:24 amsn_received
drwxr-xr-x  9 tito tito   4096 2007-07-07 00:28 .azureus
-rw-------  1 tito tito   2814 2007-07-07 21:54 .bash_history
-rw-r--r--  1 tito tito    220 2007-07-06 14:12 .bash_logout
-rw-r--r--  1 tito tito   2298 2007-07-06 14:12 .bashrc
drwxr-xr-x  2 tito tito   4096 2007-07-07 16:30 bin
drwx------  6 tito tito   4096 2007-07-07 14:22 .BitTornado
drwxr-xr-x  7 tito tito   4096 2007-07-07 14:32 .cedega
-rw-r--r--  1 tito tito   1017 2007-07-07 15:38 .cedegarc
drwx------  4 tito tito   4096 2007-07-07 14:31 .config
drwxr-xr-x  4 tito tito   4096 2007-07-07 17:47 Desktop
-rw-------  1 tito tito     26 2007-07-06 21:18 .dmrc
-rw-------  1 tito tito     16 2007-07-06 21:18 .esd_auth
drwxr-xr-x  8 tito tito   4096 2007-07-07 16:49 .evolution
lrwxrwxrwx  1 tito tito     26 2007-07-06 14:12 Examples -> /usr/share/example-content
drwxr-xr-x  2 tito tito   4096 2007-07-07 16:00 .fontconfig
drwx------  5 tito tito   4096 2007-07-07 16:49 .gconf
drwx------  2 tito tito   4096 2007-07-07 22:41 .gconfd
drwxr-xr-x 21 tito tito   4096 2007-07-06 22:06 .gimp-2.2
-rw-r-----  1 tito tito      0 2007-07-07 21:20 .gksu.lock
drwxr-xr-x  3 tito tito   4096 2007-07-06 21:19 .gnome
drwx------ 14 tito tito   4096 2007-07-07 20:32 .gnome2
drwx------  2 tito tito   4096 2007-07-06 21:18 .gnome2_private
drwxr-xr-x  2 tito tito   4096 2007-07-07 14:50 .gstreamer-0.10
-rw-r--r--  1 tito tito     86 2007-07-06 21:18 .gtkrc-1.2-gnome2
-rw-------  1 tito tito   1090 2007-07-07 16:49 .ICEauthority
drwxr-xr-x  2 tito tito   4096 2007-07-06 21:20 .icons
drwxr-xr-x  5 tito tito   4096 2007-07-07 16:30 .ies4linux
drwxr-xr-x  2 tito tito   4096 2007-07-07 19:49 Incomplete
drwx------  3 tito tito   4096 2007-07-06 22:59 .kde
drwxr-xr-x  5 tito tito   4096 2007-07-07 20:11 .limewire
drwxr-xr-x  3 tito tito   4096 2007-07-07 14:31 .local
drwx------  3 tito tito   4096 2007-07-06 23:42 .macromedia
drwxr-xr-x  3 tito tito   4096 2007-07-06 22:59 .mcop
-rw-------  1 tito tito     31 2007-07-07 15:09 .mcoprc
drwx------  3 tito tito   4096 2007-07-06 21:19 .metacity
drwx------  4 tito tito   4096 2007-07-06 23:42 .mozilla
drwxr-xr-x  9 tito tito   4096 2007-07-07 21:52 My Documents
drwxr-xr-x  3 tito tito   4096 2007-07-07 16:49 .nautilus
drwx------  3 tito tito   4096 2007-07-07 12:09 .openoffice.org2
-rw-r--r--  1 tito tito    566 2007-07-06 14:12 .profile
drwxr-xr-x  2 tito tito   4096 2007-07-07 02:04 .qt
-rw-------  1 tito tito   2314 2007-07-07 22:19 .recently-used
-rw-r--r--  1 tito tito  32434 2007-07-07 22:32 .recently-used.xbel
-rw-r--r--  1 tito tito      0 2007-07-06 21:41 .sudo_as_admin_successful
drwxr-xr-x  2 tito tito   4096 2007-07-06 21:20 .themes
drwx------  4 tito tito   4096 2007-07-06 22:05 .thumbnails
drwxr-xr-x  4 tito tito   4096 2007-07-07 14:32 .transgaming_global
drwx------ 15 tito tito   4096 2007-07-07 21:52 .Trash
drwxr-xr-x  2 tito tito   4096 2007-07-06 21:34 .update-manager-core
drwx------  2 tito tito   4096 2007-07-06 22:33 .update-notifier
drwxr-xr-x  3 tito tito   4096 2007-07-07 21:47 vmware
drwxr-xr-x  2 tito tito   4096 2007-07-07 01:39 .vmware
-rw-r--r--  1 tito tito      4 2007-07-07 21:11 .windows-label
**_drwxr-xr-x  4 tito tito   4096 2007-07-07 23:57 .wine_**
-rw-------  1 tito tito    123 2007-07-07 16:49 .Xauthority
-rw-r--r--  1 tito tito 200044 2007-07-07 17:27 .xsession-errors

Yes I did,
I already did that stuff.

---

### Post by ubuntu.daemon on 2007-07-08
lol well that proves you have it but i meant
```
user@home:/media/cdrom0$ ls -al
```

but it gives you that error??

but yeah post me that of your cd's directory and yeah we'll go from there :mad:

---

### Post by Vendetta_NZ on 2007-07-08
Quick noob question. How do you even open Wine? I installed it, but I don't know how to open it?

---

### Post by ubuntu.daemon on 2007-07-08
lol it would be 
```
user@home: winecfg
```

Now to like install something like the guy up here is, you would need to create a link from the mount point of your cd-rom drive to a windows drive.  Then do a lil install.... to set up a drive look up!
```

virgo@galactica:~$ sudo mount -o loop starcraft/starcraft.iso /media/iso/
virgo@galactica:~$ cd /media/iso/
virgo@galactica:/media/iso$ ls -al
total 587427
dr-xr-xr-x 1 root root      2048 1998-03-27 03:27 .
drwxr-xr-x 4 root root      4096 2007-07-02 23:54 ..
-r-xr-xr-x 1 root root        40 1998-01-08 20:06 autorun.inf
dr-xr-xr-x 1 root root      2048 1998-03-27 03:27 directx5
dr-xr-xr-x 1 root root      2048 1998-03-27 03:27 help
-r-xr-xr-x 1 root root 601389682 1998-03-27 02:29 install.exe
dr-xr-xr-x 1 root root      2048 1998-03-27 03:27 isp
-r-xr-xr-x 1 root root      1078 1998-01-14 00:11 sc.ico
-r-xr-xr-x 1 root root     25088 1998-01-14 00:11 setup.exe
-r-xr-xr-x 1 root root     95232 1998-01-20 07:29 smackw32.dll
virgo@galactica:/media/iso$
virgo@galactica:/media/iso$ wine install.exe
```
then i can play!
```
virgo@galactica:/media/iso$ cd /home/virgo/.wine/drive_c/Program\ Files/Starcraft/
virgo@galactica:~/.wine/drive_c/Program Files/Starcraft$ wine Star
StarCraft.exe  StarEdit.exe    
virgo@galactica:~/.wine/drive_c/Program Files/Starcraft$ wine StarCraft.exe -opengl

```

WAIT TITO!!!!! just thought of it hey when you did your,"winecfg"  did you do it like
```
user@home: sudo winecfg
```  ?????

That might be your problem, so if so delete
```
user@home: sudo rm -rf .wine
user@home: winecfg
```

then redo ur stuff bc maybe thats your problem, just not having sudo privileges because when you did it the first time!

---

### Post by ~~Tito~~ on 2007-07-08
no i just did 
winecfg
also that is the right drive. . .

---

### Post by ~~Tito~~ on 2007-07-08
bump

---

### Post by ubuntu.daemon on 2007-07-08
that was your home directory, i want the ls -al of your cd you mounted

---

### Post by ~~Tito~~ on 2007-07-08
Like i said its the right drive.

tito@TITOS-LAPTOP:~$ /media/cdrom0 ls -al
bash: /media/cdrom0: is a directory
tito@TITOS-LAPTOP:~$

---

### Post by ubuntu.daemon on 2007-07-09
lmao dude, you need to 
```
user@home: cd /media/cdrom0
user@home:/media/cdrom0$  ls -al
```

Thats what it should look like!  when you did the ls -al above you werent in the directory and didnt use a command before it.... so of course that wouldnt work... lol

im onlne for a bit now btw

---

### Post by ~~Tito~~ on 2007-07-09
Ok let me pop the cd in and ill try it.

---

### Post by ~~Tito~~ on 2007-07-09
tito@TITOS-LAPTOP:~$ cd /media/cdrom0
tito@TITOS-LAPTOP:/media/cdrom0$ ls -al
total 17255
dr-xr-xr-x 1 root root    2048 2006-10-24 14:52 .
drwxr-xr-x 3 root root    4096 2007-07-08 20:41 ..
-r-xr-xr-x 1 root root      49 2005-11-05 07:34 autorun.inf
dr-xr-xr-x 1 root root    2048 2006-10-24 14:49 DirectX
-r-xr-xr-x 1 root root 3135949 2006-10-23 16:18 EAW_Manual.pdf
-r-xr-xr-x 1 root root 6950469 2006-03-10 15:19 Empire_TechTree.pdf
dr-xr-xr-x 1 root root    2048 2006-10-24 14:49 GameData
dr-xr-xr-x 1 root root    2048 2006-10-24 14:49 Install
-r-xr-xr-x 1 root root  557056 2006-01-07 10:30 LaunchEAW.exe
-r-xr-xr-x 1 root root 7011807 2006-03-10 15:19 Rebel_TechTree.pdf
tito@TITOS-LAPTOP:/media/cdrom0$ 

The launcheaw.exe wont work with wine, so I go into game data and use the setup.exe in there, but it gives me errors.

---

