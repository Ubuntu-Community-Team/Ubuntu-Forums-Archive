---
title: "Removing unnecessary Processes"
date: 2005-09-03
forum: Desktop Environments
---

### Post by withoutme on 2005-09-03
I am a Linux newbie. I have Ubuntu 5.04 installed on my really really old laptop. I did the server installation. My computer is still slow. I would like to know if there are any unnecessary process that I can kill - during boot, after boot, in the background etc etc. Here are my spec..

Hardware: 
Toshiba Tecra 550CDT
266Mhx Pentium MMX
96Mb Ram
4GB HD

SOftware:
Ubuntu 5.04 Server installation with
XFCE4
firefox
Gaim

I still havent figured out to make my wireless work, but I want to speed up things first.. Any help please. Things like
1. How to indentify unnecessary processes
2. At boot time, in background.
Thank you again

---

### Post by arnieboy on 2005-09-03
[QUOTE=withoutme]I am a Linux newbie. I have Ubuntu 5.04 installed on my really really old laptop. I did the server installation. My computer is still slow. I would like to know if there are any unnecessary process that I can kill - during boot, after boot, in the background etc etc. Here are my spec..

Hardware: 
Toshiba Tecra 550CDT
266Mhx Pentium MMX
96Mb Ram
4GB HD

SOftware:
Ubuntu 5.04 Server installation with
XFCE4
firefox
Gaim

I still havent figured out to make my wireless work, but I want to speed up things first.. Any help please. Things like
1. How to indentify unnecessary processes
2. At boot time, in background.
Thank you again[/QUOTE]


install BUM (boot up manager)
[http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)

---

### Post by withoutme on 2005-09-04
kewl.. i will give it a try .. thank you

---

### Post by lagagnon on 2005-09-04
[QUOTE=withoutme]I am a Linux newbie. I have Ubuntu 5.04 installed on my really really old laptop. I did the server installation. My computer is still slow. 
Hardware: 
Toshiba Tecra 550CDT
266Mhx Pentium MMX
96Mb Ram
4GB HD
[/QUOTE]

You are really pushing the envelope running Ubuntu with that machine. If I were you I would forget Ubuntu and instead I would run VectorLinux ([http://www.vectorlinux.com)](http://www.vectorlinux.com)). I use both VL and Ubuntu. VL is incredibly fast and efficient on older machines (especially the new VL5.1 Standard version). It will run fast with 64MB of RAM - Ubuntu is really only happy with 256MB for the base install.

If you are adamant about using Ubuntu first thing to do is to use Fluxbox or IceWM as the window manager instead of Metacity.

---

### Post by [pl]ice on 2005-09-04
yeh, i agree with lagagnon, i go old laptop and 32 megs for me wan't enough to install even the base for ubuntu... got more ram & iceWM works ok.  and it's gonna be slow... i got 300 mhz, AND it's slow, i heard from this forum that 96 ram is really the minimum to install ubuntu! but that was with icewm.

---

### Post by withoutme on 2005-09-06
I agree, the speed is an issue. I am a newb so I am trying different things and learn linux in the process. I will get Ice tonight and see how that goes.
Also, i tried to install Bum and i got:
vj@alexis:~$ sudo apt-get install bum
Reading package lists... Done
Building dependency tree... Done
Package bum is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bum has no installation candidate
 What happened to bum?

Should I remove XFCE before i install ICE?

---

### Post by d1337 on 2005-09-06
I could be wrong, but I don't think you cant apt-get bum...at least yet.  I've not installed it, so I don't have any insight, but the link that arnieboy gave you is a good place to start.  Maybe your first try at installing without apt-get...but it'll be a good learn for you.

d1337

---

### Post by withoutme on 2005-09-06
I have tried to do that - get the .deb packages and do a dpkg on it. But a lot of dependency errors, which I am not able to figure out. One of tem was gksu, but when i tried to install gksu, it would say dependency on bum in addition to other files/packages:
sudo dpkg -i gksu_1.3.4-1_i386.deb
Selecting previously deselected package gksu.
(Reading database ... 27908 files and directories currently installed.)
Unpacking gksu (from gksu_1.3.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gksu:
gksu depends on libc6 (>= 2.3.5-1); however:
Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
gksu depends on libgksu1.2-0 (>= 1.3.3); however:
Package libgksu1.2-0 is not installed.
gksu depends on libgksuui1.0-1; however:
Package libgksuui1.0-1 is not installed.
gksu depends on libglib2.0-0 (>= 2.8.0); however:
Version of libglib2.0-0 on system is 2.6.3-1.
gksu depends on libgnome-keyring0 (>= 0.4.3); however:
Version of libgnome-keyring0 on system is 0.4.2-0ubuntu1.
gksu depends on libpango1.0-0 (>= 1.8.2); however:
Version of libpango1.0-0 on system is 1.8.1-0ubuntu2.
dpkg: error processing gksu (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gksu

I think i am going ot do an apt-get remove bum gksu and everything.. clean everything and start from installing gksu and see what happens....

---

