---
title: "Stella in 18.04"
date: 2018-09-13
forum: Emulators
---

### Post by cx40hero on 2018-09-13
Good evening, good morning & good afternoon!
I have recently installed Ubuntu 18.04 for the first timeand have started playing round with the system and installing the new softwareI require.
VLC, Gimp, OpenShot, Ardour and Audacity all work perfectlyfine on the first installation but for some unknown reason I cannot get Stella(Atari 2600 Emulator) to work?
It looks like it installs fine but when I hit run followingthe download nothing happens, I have tried going into programs and the Stellabutton is there, but again, if I click on it I get a spinny wheel for a fewseconds and then nothing&#8230;&#8230;
Does anyone know what is causing this issue?
I love playing Atari 2600 and I have been running Stella inWindows fine for years&#8230;.
Please help!
 
CX40

---

### Post by deadflowr on 2018-09-13
*Thread moved to **Emulators***

stella's execution command is stella, so if you run it from a terminal, what is the output:
```
stella
```
please post back any results it shows.

---

### Post by cx40hero on 2018-09-13
[https://youtu.be/_q45_xeVNT0](https://youtu.be/_q45_xeVNT0)

---

### Post by cx40hero on 2018-09-13
david@dday1sc:~$ stella
ERROR: Couldn't load settings file
dbus[9997]: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file ../../../dbus/dbus-message.c line 1362.
This is normally a bug in some application using the D-Bus library.

  D-Bus not built with -rdynamic so unable to print a backtrace
Aborted (core dumped)
david@dday1sc:~$ ^C
david@dday1sc:~$

---

### Post by cx40hero on 2018-09-13
NB

Sorry for just posting links and the output, where I my manners!

Thank you for any support you can offer :)

---

### Post by Dennis N on 2018-09-13
I installed it to see what's up, and didn't have any problem - using Ubuntu 18.04. First time using, but I was able to easily find some game files, loaded one, and that worked fine. (I am more familiar with atari800 program - we have used that for years.)

Did you install from the Ubuntu repository? Or something else? Possibly a different version?

Details:

```
dmn@Roxanne:~$ apt show stella
Package: stella
Version: 5.1.1-1
Priority: optional
Section: universe/otherosfs
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 6,746 kB

```

---

### Post by cx40hero on 2018-09-13
I just ran sudo apt-get install stella

---

### Post by Dennis N on 2018-09-14
> **cx40hero said:**
> I just ran sudo apt-get install stella
I did the same, so we have the same version.
> ERROR: Couldn't load settings file
The settings file would most likely be **~/.config/stella/stellarc**
Do you see any problems?
Compare my listing - check owner and permissions - can you read the file itself in a text editor?
```
dmn@Roxanne:~/.config/stella$ ls -l
total 20
drwxrwxr-x 2 dmn dmn 4096 Sep 13 12:45 cfg
drwxrwxr-x 2 dmn dmn 4096 Sep 13 12:45 nvram
drwxrwxr-x 2 dmn dmn 4096 Sep 13 13:50 state
-rw-rw-r-- 1 dmn dmn    0 Sep 13 19:27 stella.pro
-rw-rw-r-- 1 dmn dmn 5025 Sep 13 19:27 stellarc
```
The three direcories here are empty.

The line after the ERROR: line (about dbus) I can't analyze. That may not be important, just some system output you get when you use terminal. But I can't say for sure.

---

