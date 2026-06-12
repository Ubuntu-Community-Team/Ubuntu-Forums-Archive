---
title: "Danger of the deep (game) install"
date: 2012-06-22
forum: Gaming &amp; Leisure
---

### Post by auspot on 2012-06-22
I downloaded dangerdeep from: [http://dangerdeep.sourceforge.net/](http://dangerdeep.sourceforge.net/)

I used sudo now the problem is I am a beginner I have been able to download
ubuntu 11.04 32bit  and now am using it. better than windows.

Problem: when I type in terminal dangerdeep results: dangerdeep: command not found
can someone tell me how to remove all the files in terminal (dangerdeep) so I can start
over.  I tried to install again but it says its locked or something and not able to install.

I have the dangerdeep on the desktop and don't know how to run it either.
can someone give me step by step instructions 

Thanks for any help
auspot

---

### Post by howefield on 2012-06-22
Post spliced off to its own thread and moved to "*Gaming & Leisure*"

---

### Post by LinXNut on 2012-06-22
Hi auspot I downloaded this too and am gonna help ya out. So typically when you download, chances are its gonna start in your "Downloads" folder. 
Type:
```
cd Downloads
```This should show you all your downloads. Next, find the name of the ".bin" linux download. (dangerdeep-0.3.0-linux-installer.bin) 
Type:
```
chmod +x  dangerdeep*
``` The * means it executes everything with dangerdeep, but since its the only one it will only execute that one. The chmod +x made the .bin an executable, so after making it executable, type:
```
sudo ./danger*
```Follow the on screen instructions, and thats how you install it. (:

Ok I found out the problem why It wont run. There are 2 packages you have to install.
-libSDL_mixer-1.2
-libSDL_net-1.2
In the Ubuntu software center type in libsdl_mixer and install it, but make sure it is not the "dev." Same goes for libsdl_net. Also, when running the dangerdeep executable, make sure you type "sudo" first or it wont work.

I hope this helps! :D

---

### Post by auspot on 2012-06-22
I have ubuntu 11.04 32 bit.

cd downloads don't work   what next or how do I get the cd to work ?

Thanks for the help
auspot

---

### Post by december0123 on 2012-06-22
These commands are case sensitive. ```
cd downloads
``` may not work, but ```
cd Downloads
``` will.

---

### Post by auspot on 2012-06-22
cd Downloads did not work either: 

bill@bill-ET1831:~$ cd Downloads
bash: cd: Downloads: No such file or directory

next?

auspot

---

### Post by december0123 on 2012-06-22
Try ```
 cd ~/Downloads
```If this doesn't work....What language is set in your system? If it's not english, instead of "Downloads" type the name of that folder in your language. You can see what it's called by opening your home folder: ```
cd ~
ls    
``` -command line way

"cd ~" opens the home folder
"ls" lists directory contents

or just by opening your file manager and seeing the folders on the left side -gui way.

---

### Post by auspot on 2012-06-22
bill@bill-ET1831:~$ cd
bill@bill-ET1831:~$ ls
dangerdeep  Documents         Firefox_wallpaper.png  Pictures  Templates
Desktop     examples.desktop  Music                  Public    Videos
bill@bill-ET1831:~$ 

cd get nothing but ls shown above now what do I do?

---

### Post by Perfect Storm on 2012-06-22
Just create the folder Downloads if it doesn't exist.

---

### Post by auspot on 2012-06-22
bill@bill-ET1831:~$ cd
bill@bill-ET1831:~$ ls
dangerdeep  Documents         Firefox_wallpaper.png  Pictures  Templates
Desktop     examples.desktop  Music                  Public    Videos
bill@bill-ET1831:~$ cd dangerdeep
bill@bill-ET1831:~/dangerdeep$

is there a command or something that will run dangerdeep?

---

### Post by oldrocker99 on 2012-06-24
Here's what I get when I run

~/dangerdeep$ scons debug=1 datadir=`pwd`/data 
scons: Reading SConscript files ...
Compiling for GNU/Linux Environment (linux2)
Using architecture: x86_64
ERROR: no libGL.so detected!
grep: libGL.so: No such file or directory
GL headers declare glBindProgram, but libGL.so has no such symbol! Ignoring all undefined symbols...
Install binary path: /usr/local/bin
Using data dir: /home/oldrocker99/dangerdeep/data
Checking for C library GL... no
Library GL is missing, it must be installed!


I have libGL.so in /usr/lib/x86_64-linux-gnu/, among otrher directories, but the Sconstruct file, while it searches /usr/lib, doesn't apparently dig deeper into the directories.](*,)

Dependency hell?

---

### Post by Dlambert on 2012-06-25
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```

---

### Post by oldrocker99 on 2012-06-25
Well, 

sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
[sudo] password for oldrocker99: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-dev is already the newest version.
libglu1-mesa-dev is already the newest version.
libglu1-mesa-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Now what???

---

### Post by pd12 on 2012-10-02
Hi, 

read the stuff here and my comment for Ubuntu 12.04
basically change lib64 directory in the SConstruct file to the one your system uses. 

[https://sourceforge.net/tracker/index.php?func=detail&aid=3522925&group_id=71244&atid=535546](https://sourceforge.net/tracker/index.php?func=detail&aid=3522925&group_id=71244&atid=535546)

---

