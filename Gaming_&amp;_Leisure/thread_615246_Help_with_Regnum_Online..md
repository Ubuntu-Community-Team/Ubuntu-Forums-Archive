---
title: "Help with Regnum Online."
date: 2007-11-16
forum: Gaming &amp; Leisure
---

### Post by -gabe-noob- on 2007-11-16
Note: I'm a NOOOB 

Ok 
so I want to play regnum natively on linux. Being the noob that I am, I cannot figeur out how to do this, can some one help me? I'm used to windows graphical installs.

---

### Post by Tyke91 on 2007-11-16
follow the readme in the .tar.gz file that you download regnum in 


most things that you need will have automatic or graphical installs. for some rare things you will need to compile the source code first. It's pretty easy to do.

after you have your downloaded file from regnum's website

first, create some directory. probably called /home/INSERTYOURUSERNAMEHERE/regnum

by copy/pasting this code
```
mkdir ~/regnum
```then use the graphical unpacking tool to extract the contents of the .tar.gz file. extract it to your /home/yourusername/regnum directory (you just made it with the above code, ~/ is a shortcut to your home folder)

then type these codes

```
 cd ~/regnum
```(changes the "place" that you are in your computer to your new ~/regnum directory
```
./configure
```configures the files needed to compile the code
```
make
```makes the install file
```
make install
```installs your program

that should give you regnum. enjoy.

NOTE: I'm not sure if extracting regnum creates it's own regnum directory with all the stuff inside, or if it just creates the mess of files. If it creates it's own directory, then you can do cd ~/regnum/WhatEverTheNameOfTheNewFileIs instead of just cd ~/regnum

---

### Post by Felson on 2007-11-17
The Download from the site was binary for me, so what you need to do is.

```

mkdir ~/regnum
 cd ~/regnum
wget http://www.regnumonline.com.ar/downloads/files/rolauncher.tar.gz
tar xzf rolauncher.tar.gz
./rolauncher

```

After that you are all GUI.

---

### Post by Tyke91 on 2007-11-17
it's a binary now? sweet! it's been so long since I downloaded it...

---

### Post by -gabe-noob- on 2007-11-17
You guys are awsome, thanks. Just one question (this may make you facepalm so beware) How do i get to the Gui installer after I enter that code in the terminal?

---

### Post by gcrussell1 on 2007-11-18
If you run that code one line at a time, it will create a regnum directory, take you there, download the installer, extract the installer, and run the installer - the installer run from the terminal should bump you automatically (or after a couple simple yes/no questions) into the GUI installation interface, with the terminal running behind it.

If you can't get to the installer with these instructions, check if a new directory was created in your ~/regnum directory when you extracted the installer.

You should also be able to run "sudo ./rolauncher" to install Regnum for all users on the computer, instead of limiting it to the account that's currently logged in.

---

### Post by regor210 on 2007-11-18
i had to use "$ MALLOC_CHECK_= ./rolauncher" to get it to work with gusty 7.10 Ubuntu and Kubuntu.

---

### Post by Felson on 2007-11-18
I found a link to a 64bit version. I couldn't get sound to work with the standard install, but this one works awesome for me.

[64bit]("http://www.regnumonline.com.ar/downloads/files/rolauncher64.tar.bz2")

---

### Post by SpectralDesign on 2007-11-22
I tried this, but I just get a coredump :(

~/regnum$ ./rolauncher 
*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08666dd0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77e9d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb77ed800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb76f9961]
./rolauncher[0x817613d]
./rolauncher[0x8070b53]
./rolauncher[0x8065a7a]
./rolauncher[0x8067ed1]
./rolauncher[0x810074e]
./rolauncher[0x805c55e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7796050]
./rolauncher(__gxx_personality_v0+0x3d5)[0x805c391]
======= Memory map: ========

blah blah blah

b7f25000-b7f2c000 r--s 00000000 08:01 8279130    /usr/lib/gconv/gconv-modules.cache
b7f2c000-b7f2e000 rw-p b7f2c000 00:00 0 
b7f2e000-b7f48000 r-xp 00000000 08:01 819221     /lib/ld-2.6.1.so
b7f48000-b7f4a000 rw-p 00019000 08:01 819221     /lib/ld-2.6.1.so
bf914000-bf929000 rwxp bf914000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

---

### Post by wingit on 2007-11-28
i got the same thing how do you fix?

---

### Post by AranelSurion on 2007-12-01
@spectraldesign , wingit

Try this : "MALLOC_CHECK_=0 ./rolauncher"

---

### Post by SpectralDesign on 2007-12-01
AranelSurion -

Thanks, that seems to be working! (I'll know for sure once it finishes downloading resources, but so far so good!)

---

### Post by SpectralDesign on 2007-12-02
Yep that works -- I have to drop all details levels to the minimum, but it works :)

---

### Post by IeU on 2007-12-10
thanks for the help,

it seems to be working now :)

---

### Post by Lord DarkPat on 2007-12-18
help!!!!!!
It says that
1)My grfix card is old(not possible, ran in windows)
2)NO drivers(installed them already)
3)No DirectX(does that even exist for linux?)

---

### Post by Ferrat on 2007-12-18
> **Lord DarkPat said:**
> help!!!!!!
It says that
1)My grfix card is old(not possible, ran in windows)
2)NO drivers(installed them already)
3)No DirectX(does that even exist for linux?)

You sure you didn't by accident run the windows version in wine or something like that?

---

### Post by Lord DarkPat on 2007-12-18
I ran rolauncher. Is that wine?

---

### Post by Lord DarkPat on 2007-12-19
help!!!!!

---

### Post by HotCocoa on 2007-12-29
Yes, I had that problem with the core dumping too.  But now, when I try to run that command, it will not completely load the game.

EDIT: Nevermind! It was a one-time bug!

---

### Post by zelrikriando on 2008-08-12
Why does it want to run it with Wine???????????? I downloaded the Linux version I am sure !

---

