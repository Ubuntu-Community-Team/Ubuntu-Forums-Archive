---
title: "Amarok crashing"
date: 2005-08-11
forum: Desktop Environments
---

### Post by Heretic09 on 2005-08-11
Amarok was working fine the first time I ran kubuntu. I haven't used it for a while and i've run countless updates to various packages. Now everytime I try to start it I get:

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!

I've also noticed that VLC has stopped working as well. Reinstalling Amarok did not fix anything.

Any help would be appreciated.

---

### Post by arcanistherogue on 2005-08-11
Yeah, I got alot of errors with amaroK too.  I just started using JuK, its a bit more minimal and it works fine.  Plus it is a KDE app so it looks nice.

---

### Post by Heretic09 on 2005-08-11
I don't know what went wrong, it was working fine even after I upgraded to kde 3.4.2. Then I didn't use it for a while and now it won't start. I'm using Juk now as well and noatun as a video player.

---

### Post by Heretic09 on 2005-08-11
I'm pretty sure a lot of the problems I had is rfom installing from ftp.nerim.net when I first installed kubuntu. Is there any way to find out which package was installed from which repo?

---

### Post by Submerged on 2005-12-26
It seems as though the problem is the amarok config file got corrupt.

Fix: rm /home/user/.kde/share/config/amarokrc

Please note that this will delete all previous config options; if anyone has a fix for this by editing amarokrc please let me know

edit: seems like it still crashes, but after the wizard...so no help

---

### Post by anil_robo on 2005-12-27
I read somewhere in the forums that amaroK would run better under KDE environment rather than GNOME. I am now fed up with amaroK crashes on GNOME, and I can't switch to KDE because that doesnt suit my preferences. I guess someone should fix amaroK crashes in GNOME in the next release. I have uninstalled amaroK completely, and use XMMS extensively.

---

### Post by willPower on 2006-01-15
Uninstalling sqlite altogether fixed the problems I was having with amaroK. For some reason I started getting "database schema has changed" and "database disk image is malformed" errors when trying to run amaroK and it would never start completely.

It runs great now.

---

### Post by apswartz on 2006-01-21
[QUOTE=anil_robo]I read somewhere in the forums that amaroK would run better under KDE environment rather than GNOME. I am now fed up with amaroK crashes on GNOME, and I can't switch to KDE because that doesnt suit my preferences. I guess someone should fix amaroK crashes in GNOME in the next release. I have uninstalled amaroK completely, and use XMMS extensively.[/QUOTE]

I am getting the same crash messages in KDE...

alan@omicron:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!
alan@omicron:~$ /usr/lib/amarok/amarokapp
Segmentation fault
alan@omicron:~$

---

### Post by apswartz on 2006-02-03
I have even uninstall the packages and compiled the program for myself. 

SAME ERRORS!!!!

Deleting the old settings doesn't help. I am also having seg faults in gwenview and digikam.

---

### Post by Mayfairy on 2006-02-05
I'm having these same problems every now and then. Usually I'll get AmaroK working again when I reboot my machine. 
Whenever AmaroK starts doing this then Wine will do the same. 
I'm using Ubuntu 5.10 with Gnome desktop. Same thing happened with 5.04 and with two different machines.

---

### Post by taniwhaiti on 2006-02-12
my amarok is crashing when scanning the collection.

Amarok scans automagically, as well as on request.

There's a tag in a music file somewhere that crashes taglib, and takes amarok with it. (actaully, it was several files). I moved those out of the scanned directory.

cat ~/.kde/share/apps/amarok/collection_scan.log

The last entry, following an amarok crash, is likely to be the file that crashing amarok 

(if that is what is crashing your amarok also)

---

### Post by fshaked on 2006-02-28
Had the same problem, amarok and vlc do not start (try configuring your screen saver...).
 
HERE'S HOW I FIXED IT: install nvidia-glx (that's it)

---

### Post by coldwiston on 2006-04-10
I'm having the same problems, not got a clue why it started, but seemed to coincide with my switching the display manager to kdm, then upgrading the kernel to k7 architecture (everything appeared to work after switching to kdm and before kernel upgrade, but i didnt test amaroK!)

The only thing I noticed is that libtag gives errors when i boot the computer (something about not being symbolic links), but i can't find these in the logs. I'm guessing that could well be the problem, but reinstalling libtag didnt fix the error...

I can't reinstall everything at the moment, so unless someone has any good ideas for solving this, I'll just have to make do with VLC for a while. Looking forward to getting amaroK back!!!

I might try creating a test user, see if it's my profile settings causing the problem, and booting with my old stock kernel. That nvidia-glx sounds interesting as well (i remember how nvidia drivers used to cause hell in other distros) so i'll try reinstalling that too

Any other ideas?

---

### Post by adamkane on 2006-04-10
Install alsa-oss and taglib-1.4.

---

### Post by Tragos on 2006-05-10
[QUOTE=fshaked]Had the same problem, amarok and vlc do not start (try configuring your screen saver...).
 
HERE'S HOW I FIXED IT: install nvidia-glx (that's it)[/QUOTE]

Thank you! That worked for me, too.

---

### Post by bluenova on 2006-06-08
I have the same errors, as others in this thread, but it was working fine until I installed kubuntu-desktop to check it out. I thought about removing the amarok config file, to see if that was the problem, but it didn't help. KDE seems to run fine, but there are icons missing in the KDE menu, and amarok does not run in KDE either.

Any ideas?

p.s. I have nvidia-glx installed.

---

### Post by bluenova on 2006-06-11
Update

Amarok will run fine in a differn't user area, just not in mine. I have tried clearing out all files related in amarok in my /home dir but it didn't help. The output I get from terminal is:

```
$ amarok
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
ScimInputContextPlugin()
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3600062
KCrash: Application 'amarok' crashing...
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

### Post by bluenova on 2006-06-11
If I run sudo amarok, it also runs fine with this output:

```
sudo amarok
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-root/kconf_updateN4VVac.tmp:1
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
ScimInputContextPlugin()
amarok: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml

```

---

