---
title: "quake III arena"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by Ziggyz on 2007-08-08
Ok, This is a really n0b question, but I bought a game from tux games, you know designed for linux. It wont.... lets say, work? I click on setup.sh, nothing happens. Then quake3.sh, nothing happens. I tried in console, and its like sh: cant open setup, sh: cant open quake3.

The readme on installation doesn't help. And the support e-mail bounced. I was wondering if there was any way to install whats on this game.

This is what is on the cd

[IMG]http://i7.photobucket.com/albums/y288/getcrunkfoo/pics/quake3.png[/IMG]

---

### Post by DoktorSeven on 2007-08-08
Open a terminal and do

cd /media/cdrom0
sudo bash setup.sh

---

### Post by Cappy on 2007-08-08
Maybe Try
```

sudo bash /media/cdrom0/setup.sh

```

or

```

cp /media/cdrom0/setup.sh ~/Desktop/
cd ~/Desktop
chmod +x setup.sh
sudo su
./setup.sh

```

---

### Post by BillBlackett on 2007-08-11
OK - Another NooB here,

I managed to get through the installation OK, but then when I go to run it, I get a "Can't find default.cfg" error.

Now I know that the directory in the search path /root/.q3a/baseq3 doesn't exist, but when I'm logged in as bill the search path bill/.q3a/baseq3 doesn't exist either.

What the heck am I supposed to do?

Here's my console script:

> bill@bill-desktop:/media/cdrom0$ su
Password: 
root@bill-desktop:/media/cdrom0# quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/root/.q3a/baseq3
quake3/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/root/.q3a/demoq3
quake3/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Error: Couldn't load default.cfg


---

### Post by Sockerdrickan on 2007-08-11
Q3 1.11 linux-i386 Nov 24 1999

I would recommend getting the latest source port 1.34 [www.ioquake3.org](www.ioquake3.org) for better experience

---

### Post by Ziggyz on 2007-08-11
Aight, thanks for the help on the installation. I tried the same command to get the game running and it dident work.

```
ziggy@ziggy-desktop:~$ cd /media/cdrom0
ziggy@ziggy-desktop:/media/cdrom0$ sudo bash quake3.sh
quake3.sh: line 67: bin/x86/glibc-2.1/quake3: Permission denied
No Quake3 binary for x86/glibc-2.1

Please contact Loki Technical Support at support@lokigames.com

```

I don't know what to do past this point.

---

### Post by Sockerdrickan on 2007-08-11
If you have installed it just type quake3

---

### Post by Ziggyz on 2007-08-11
Ok, now it is saying

```
ziggy@ziggy-desktop:~$ quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/baseq3
quake3/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/demoq3
quake3/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Error: Couldn't load default.cfg
ziggy@ziggy-desktop:~$ 

```

I can also guarentee I bought the game, not the demo. Ill referr to what you posted above though.

*Edit it said sh: ioquake3: not found after it installed, now what?
double edit* Now it says "./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory" after ire installed using symbolics in the directory.

---

### Post by Sockerdrickan on 2007-08-11
Yes, install openal! ;) Great sound API

---

### Post by Ziggyz on 2007-08-14
? how can i get the game to run?

---

### Post by Sockerdrickan on 2007-08-14
install openal of course it's in synaptic libopenal0a

---

### Post by Ziggyz on 2007-08-14
doesent work

still gives
```
ziggy@ziggy-desktop:~$ quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/baseq3
quake3/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/demoq3
quake3/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Error: Couldn't load default.cfg

```

---

### Post by Sockerdrickan on 2007-08-14
[http://www.ioquake3.org/files/ioquake3-1.34-rc3.run](http://www.ioquake3.org/files/ioquake3-1.34-rc3.run) You have 1.11 and that's 1.34! Should fix the problem

---

### Post by Ziggyz on 2007-08-15
still... doesent work. After install, it asked if I wanted to run the game, and this happened.

```
ioQ3 1.34-rc3 linux-i386 Nov 28 2006
----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/baseq3
/usr/local/games/ioquake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/ioquake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/ioquake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/ioquake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/ioquake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/ioquake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/ioquake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/ioquake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/ioquake3/baseq3

----------------------
534 files in pk3 files
Sys_Error: Couldn't find pak0.pk3. Check that your Q3
executable is in the correct place and that every file
in the baseq3 directory is present and readable.
ziggy@ziggy-desktop:~$ 

```

the game still dident run afterwards, either by that thing I installed, or this.

```
ziggy@ziggy-desktop:~$ quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/baseq3
quake3/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ziggy/.q3a/demoq3
quake3/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Error: Couldn't load default.cfg

```

---

### Post by Sockerdrickan on 2007-08-15
=) put pak0.pk3 in /home/ziggy/.q3a/baseq3

---

### Post by Cochise on 2007-08-15
you have to copy all the .pak files from the base folder on the cd to the games data directory.

---

### Post by Sockerdrickan on 2007-08-15
Its only one

---

### Post by Ziggyz on 2007-08-17
Nice it works, but I hear no sound, whats up with that?

---

