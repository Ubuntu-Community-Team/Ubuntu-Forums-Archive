---
title: "nvidia driver"
date: 2005-12-22
forum: Desktop Environments
---

### Post by ikki_72 on 2005-12-22
got gcc-4.0_4.0.1-4ubuntu9_i386.deb, done 'dpkg -i' it without failing but when i tried to 'sh' NVIDIA-Linux-x86-1.0-8174-pkg1.run but before it started to install it displayed this:
warning: skipping the runlevel check (the utility 'runlevel' failed to run)
no precompiled kernel interface was found to match your kernel...

i hit the ok then this showed up:
gcc-version-checkfailed:
./usr/src/nv/conftest.sh: line 19: cc: command not found
could not compile gcc-version-check.c



i'm kinda fed up with all the downloading packages one by one. i almost gone nuts. any place where i can downloaded the latest 'wholesome' package foe breezy?

---

### Post by 23meg on 2005-12-22
Before running the driver installer, did you do this?```
CC=gcc-3.4
export CC
```

---

### Post by MartinG on 2005-12-22
[QUOTE=ikki_72]i hit the ok then this showed up:
gcc-version-checkfailed:
./usr/src/nv/conftest.sh: line 19: cc: command not found
could not compile gcc-version-check.c

i'm kinda fed up with all the downloading packages one by one. i almost gone nuts. any place where i can downloaded the latest 'wholesome' package foe breezy?[/QUOTE]You need the relevant linux headers, the build-essential package and gcc 3.4 to install this driver, and you also need to remove the restricted kernel modules as they generate a conflict.  Are you sure you want to do all this? :-) The packaged NVidia drivers (sudo apt-get install nvidia-glx) are pretty good.  If you do want to install 8174, run the following:```
sudo apt-get install build-essential
sudo apt-get install gcc-3.4
sudo apt-get install linux-headers-`uname -r`
sudo apt-get remove linux-restricted-modules-`uname -r`
export CC=gcc-3.4
sh NVIDIA....run
```

---

### Post by ikki_72 on 2005-12-24
no, never. i'd do that thanx.:KS

---

### Post by ikki_72 on 2005-12-28
ekk...didn't work. i guess either i had to reinstall ubuntu or updating my ubuntu which will happened another hundred years:(

---

### Post by MartinG on 2005-12-28
Oh .. sorry about that :-( What messages this time (if you want to pursue it further)?

---

### Post by ikki_72 on 2005-12-29
same ol same, i guess it's the way i installed it. i used expert boot prompt eventhough i knew little of linux.

---

### Post by MartinG on 2005-12-29
R-e-a-l-l-y sorry, I'm just flying on guesswork now, so I'll not offer any more thoughts.

If you do re-install and it happens again, try launching a fresh thread to see if anyone else has better ideas.

All the best.

---

### Post by cdr377 on 2005-12-29
Hi, I'd like to persue it further because I'm having the same problems. I don't want the nvidia-glx I'd rather have the official driver from nvidia because it's a lot faster. I've been trying to get it working and I have the same errors. However, I am using kubuntu 5.10 I don't know if that matters but I'm downloading ubuntu anyways and am gonna try it on there. So, all I have to do is install the kernel headers, install libc development packages, install binutils and then run the commands you've posted? So it doesn't matter if I have the latest version of gcc as long as I run the command export CC=gcc-3.4? I'll try what you've posted so far. If you have any other sugestions or help I'd appreciate it. Thanks! 

Oh, one other quick thing, is there a why to get the kde desktop installed once I've installed ubuntu 5.10? In the 5.04 versions all you had to do was apt-get install ubuntu-desktop or kubuntu-kestop but that doesn't work anymore. THanks again!

Chris R

---

### Post by MartinG on 2005-12-29
[QUOTE=cdr377]Hi, I'd like to persue it further because I'm having the same problems. I don't want the nvidia-glx I'd rather have the official driver from nvidia because it's a lot faster. I've been trying to get it working and I have the same errors. However, I am using kubuntu 5.10 I don't know if that matters but I'm downloading ubuntu anyways and am gonna try it on there. So, all I have to do is install the kernel headers, install libc development packages, install binutils and then run the commands you've posted? So it doesn't matter if I have the latest version of gcc as long as I run the command export CC=gcc-3.4? I'll try what you've posted so far. If you have any other sugestions or help I'd appreciate it. Thanks! [/quote]First, nvidia-glx IS an official NVidia driver, it's just an older and to be honest more stable version (7667, I think).

Second, Kubuntu/Ubuntu doesn't matter.  FWIW, I use Kubuntu 5.10

AFAIK, you don't need to install libc development or binutils as separate packages.  Build-essential covers all you need apart from gcc-3.4 and the kernel headers.  And yes, you can have any number of other versions of gcc installed, as long as you use export CC=gcc-3.4 before running the NVidia installer.  

Just for completeness sake, my instructions assume you have already downloaded and unpacked the Nvidia installer from their website. And, you might need to run the Nvidia installer with sudo (I can't remember!).


> Oh, one other quick thing, is there a why to get the kde desktop installed once I've installed ubuntu 5.10? In the 5.04 versions all you had to do was apt-get install ubuntu-desktop or kubuntu-kestop but that doesn't work anymore. THanks again!

Chris RI'm puzzled here. AFAIK apt-get install kubuntu-desktop still works -- did you get an error message?

---

### Post by cdr377 on 2005-12-29
I downloaded the .run file that I simply type sh and the file name and it should install right? There's no unpacking I just download the .run file. Next I do what you suggested then I try to install it with sh. I'm assuming we're thinking of the same nvidia file. Unless there's something else I'm not getting. I already tried it once in kubuntu and it didn't work. Or course I did other stuff before hand So I'm gunna install a fresh version of ubuntu and try it again your way.

---

### Post by MartinG on 2005-12-30
Sorry, you're quite right, there's no unpacking needed.

It *should* work -- but in the end I am not an expert, just a user who has found the hard way what worked for me, and which others have since said worked for them.  There's always a chance that it might not work for you, but give it a try:-)

---

### Post by nate8199 on 2006-01-03
I'm noob and have done all that was said in earlier posts in this thread

when installing it gives me an error

Unable to find kernel source tree for the currenly running kernel

---

### Post by MartinG on 2006-01-04
You also need to install the source code, then. Which is odd, as I didn't, but that's life.  If you do```
sudo apt-get install linux-source
``` you'll get an error message listing what's available, e.g.:```
Package linux-source is a virtual package provided by:
  linux-source-2.6.12 2.6.12-10.25
```Repeat the input with the version number, e.g.:```
sudo apt-get install linux-source-2.6.12
```The major thread in the forum that you could also check is
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
What we're doing here is "Method 2".

---

### Post by mo_x on 2006-01-04
You need to install linux-headers-...
There are some howto's on this forum for installing the nvidia drivers, please take a look at them.

---

### Post by Brynster on 2006-01-04
You could do a search for Automatix

Its a small application that has the ability to install the latest Nvidia driver as well as a few other apps by simply ticking a box and clicking OK.

It worked great for me.

---

### Post by MartinG on 2006-01-05
[QUOTE=Brynster]You could do a search for Automatix

Its a small application that has the ability to install the latest Nvidia driver as well as a few other apps by simply ticking a box and clicking OK.

It worked great for me.[/QUOTE]Automatix only installs the latest driver that's been added to the repositories, not the very latest from the NVidia website.

---

