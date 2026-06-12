---
title: "nvidia drivers..."
date: 2005-07-29
forum: Desktop Environments
---

### Post by da_unruled on 2005-07-29
So far my ubuntu works alright, but there are 2 things which I want to (try) to fix.

1. installing nvidia drivers.
2. trying to get dualmonitors to work.
(3. get xmms or another player working, so far only rhythmbox works)
-----
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

installing the nvidia driver according to that guide, doesn't seem to work, here is what 'went wrong'.

> 
unruled@unruled:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-settings nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/3052kB of archives.
After unpacking 9986kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 59467 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.7174-0ubuntu1_i386.deb) ...
Setting up nvidia-glx (1.0.7174-0ubuntu1) ...
Creating NVIDIA TLS links... done.

unruled@unruled:~$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 503kB of archives.
After unpacking 1032kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted nvidia-settings 1.0-3ubuntu2  [503kB]
Fetched 503kB in 1s (321kB/s)

Preconfiguring packages ...
Selecting previously deselected package nvidia-settings.
(Reading database ... 59505 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu2_i386.deb) ...
Setting up nvidia-settings (1.0-3ubuntu2) ...

unruled@unruled:~$ sudo cpt /etc/x11/xorg.conf /etc/x11/xorg.conf_backup
sudo: cpt: command not found
unruled@unruled:~$ sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf_backup
cp: cannot stat `/etc/x11/xorg.conf': No such file or directory

(I made a typo with the cpt thing, but for the rest, it says "no such file", and I cannot go on with the installation. :-? 

any help would be greatly appreciated.

---

### Post by MrCheese on 2005-07-29
X11 not x11 - it matters!!

---

### Post by da_unruled on 2005-07-29
[QUOTE=MrCheese]X11 not x11 - it matters!![/QUOTE]
 okay, it installed now. is linux always case sensitive?

I do not see a nvidia settings button though where it says there should be, even after ctrl-alt-backspacing.
I will reboot just in case now...

edit: even after a reboot, there is no nvidia settings....

> Applications -> System Tools -> NVIDIA Setting 
its not there...
the nvidia logo screen did show up though, so I assume its installed now? or not completely? ( I did the mod now so I don't get the nvidia screen each time, but yeh).
Im lost...
 :???:

---

### Post by strikeforce on 2005-07-29
The command for nvidia-settings is just that nvidia-settings.

---

### Post by da_unruled on 2005-07-29
[QUOTE=strikeforce]The command for nvidia-settings is just that nvidia-settings.[/QUOTE]
ah, okay...its just that the guide said it would be in the applications menu, but it wasn't.

the command you gave me worked :)

now.... I have a second nvidia (pci) card in my pc, for dualmonitor purposes, but it is not installed/working/enabled.
Can anyone help me with that?

---

