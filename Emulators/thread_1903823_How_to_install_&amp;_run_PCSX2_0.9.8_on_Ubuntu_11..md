---
title: "How to install &amp; run PCSX2 0.9.8 on Ubuntu 11.10 x64?"
date: 2012-01-03
forum: Emulators
---

### Post by emptycoder on 2012-01-03
Hello everyone, I'm having a problem with PCSX2 emulator, I searched everywhere but it seems I can't find any solution, hopefully someone would help me here.
I did installing the folllowing (The Required Dependencies) with this command:
```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```Also this one:
```
sudo apt-get install libglu1-mesa-dev
```The SVN:
```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```Finally build it:
```
cd pcsx2 
sh build.sh all
```After that, I didn't know what to do, there was supposed to be a file named PCSX2 to launch the emulator, but it seems I can't find it anyway, I search PCSX2 folder on Home folder and there was nothing like that.

I'm not a Linux Expert, kinda newbie... but I do have a good background, so please, somebody could tell me what's going on?
Thanks.

---

### Post by 2F4U on 2012-01-03
It seems as if there is a ppa available for pcsx2:

[https://launchpad.net/~gregory-hainaut/+archive/pcsx2.official.ppa]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa")

Any reason why you don't use that?

---

### Post by emptycoder on 2012-01-03
I have added the PPA you mentioned, but I still can't find PCSX2 file to launch the Emulator, there's a document file named INSTALL which it says that after installing the emulator all I need is launch PCSX2.
Any Ideas?

---

### Post by WienerWuerstel on 2012-01-03
> **emptycoder said:**
> I have added the PPA you mentioned, but I still can't find PCSX2 file to launch the Emulator, there's a document file named INSTALL which it says that after installing the emulator all I need is launch PCSX2.
Any Ideas?

Adding the PPA is not enough. You need to actually install the Program too.
```
sudo apt-get update
sudo apt-get install pcsx2
```

---

### Post by emptycoder on 2012-01-03
I think I installed it, there's pcsx2 folders on home and bin,but i tried that command anyway and it didn't work.

Package pcsx2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'pcsx2' has no installation candidate

---

### Post by WienerWuerstel on 2012-01-03
> **emptycoder said:**
> I think I installed it, there's pcsx2 folders on home and bin,but i tried that command anyway and it didn't work.

Package pcsx2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'pcsx2' has no installation candidate

Could you try this then?
```
sudo apt-get install pcsx2.snapshot
```

This installs a fresher Version and maybe this one will work.
I doubt it tough because the Dev's even say that pcsx2 doesn't work on 64bit Ubuntu (or just really bad).

---

### Post by satanselbow on 2012-01-03
Last time I installed it (rapidly removed from my machine due to lack of juice - my fault not theirs) I decompiled the Arch linux PKGBUILD from the AUR and documented it, for my own purposes, in Ubuntu speak :D

Unfortunately I've had a hdd failure since then but will try and dig it out of the backup if you are still struggling in the morning ;)

---

### Post by emptycoder on 2012-01-03
> **WienerWuerstel said:**
> Could you try this then?
```
sudo apt-get install pcsx2.snapshot
```This installs a fresher Version and maybe this one will work.
I doubt it tough because the Dev's even say that pcsx2 doesn't work on 64bit Ubuntu (or just really bad).

no luck!

E: Unable to locate package pcsx2.snapshot
E: Couldn't find any package by regex 'pcsx2.snapshot'

I'm not sure about 64 thing, nothing says that it will not work on 64 system, i checked the official website and docs.
Besides, I installed ia32-libs, but maybe you're right.
Any more ideas?

---

### Post by WienerWuerstel on 2012-01-03
> **emptycoder said:**
> no luck!

E: Unable to locate package pcsx2.snapshot
E: Couldn't find any package by regex 'pcsx2.snapshot'

I'm not sure about 64 thing, nothing says that it will not work on 64 system, i checked the official website and docs.
Besides, I installed ia32-libs, but maybe you're right.
Any more ideas?

I didn't say that it doesn't work at all with 64bit but...

"Ubuntu miss most of ia32libs used by pcsx2, so only 32bits package will be provided."

This is the quote from the PPA Page that says that Ubuntu doesn't provide the needed 32bit libs to make pcsx2 work. There are only 2 Solutions which I can provide you and may or may not work:

1. Run pcsx2 from the terminal and look at which libs it's missing, download them somehow and install them until it works.

1. Install 32bit Ubuntu and be a happy Camper ;)

---

### Post by emptycoder on 2012-01-03
i have no idea how to run pcsx2 from terminal, sounds like pcsx2 is not installed at all! maybe im typing the wrng command, i really don't know
the second option is a real pain, this a huge sacrifice that i don't want to make.
im simply want to find a way to launch pcsx2, thats all, everything seems to me installed well.
it would be very helpful if anyone could provide step-by-step on how installing pcsx, maybe i missed something.
anyway, thanks for help, i will leave this thread open in case someone came with a solution.

---

### Post by thatguruguy on 2012-01-03
If you're looking for a build of pcsx2 that work on 64-bit, you should install [this ppa]("https://launchpad.net/%7Emicove/+archive/console") maintained by "micove." He also maintains current builds for Dolphin-Emu (which emulates the Nintendo Gamecube and Wii), if you're into that kind of thing.

---

### Post by tkabir11 on 2012-01-04
> **emptycoder said:**
> no luck!

E: Unable to locate package pcsx2.snapshot
E: Couldn't find any package by regex 'pcsx2.snapshot'

**I'm not sure about 64 thing, nothing says that it will not work on 64 system, i checked the official website and docs.**
Besides, I installed ia32-libs, but maybe you're right.
Any more ideas?

I dont know if you have missed this- but it actually says on [this compilation guide]("http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux") that only 32bit OS is supported.

---

### Post by quequotion on 2012-01-04
I've had my own nightmares trying to compile this for amd64.

Supposedly, multiarch will someday fix this kind of problem.

At the moment, installing all the necessary :i386 libraries might get the program working, but compiling is another monster. In order to install all of the :i386 libraries necessary to both compile and run the program you will have to remove nearly every amd64 library and software package on your system.

Unless you use **getlibs**. Getlibs will install the :i386 software and libraries you need, usually without a lot of fuss.

Unfortunately, the script is not well supported and the installed files can't be as easily uninstalled.

---

### Post by mattdlyons00 on 2012-01-08
You need to set up a chroot enviroment

---

### Post by thatguruguy on 2012-01-08
> **mattdlyons00 said:**
> You need to set up a chroot enviroment

Or, use the ppa I already mentioned above.  It includes the proper 32-bit libraries as dependencies, so that pcsx2 will run on a 64-bit OS.

But, you know. Do what you feel.

---

### Post by quequotion on 2012-01-20
> **mattdlyons00 said:**
> You need to set up a chroot enviroment

Better explained as:

Set up a completely new install of Ubuntu inside your current install, using only the termial.
Start by installing one of several varios chroot clients with unintelligible but very important differences and then create an entirely new linux installation starting with debbootstrap.
Next, you need to install within that system all the librariy and software package necessary to compile pcsx, which includes all the dependent libraries and software of those packages, without any help from the PCSX2 team who don't care if you can't mystically understand what those dependencies are.
Once you've finished all that prep work, you may be ready to compile PCSX2 but it still probably won't work and furthermore you still have to log in to your chroot whenever you want to play PCSX2.

*Yes I have actually done this*, and no I do not think it is a viable solution under any circumstances.

---

### Post by quequotion on 2012-02-12
> **thatguruguy said:**
> use the ppa I tried this. PCSX2 crashes and the opengl plugin says something about my hardware possibly not being enough. That is unlikely, not impossible, but unlikely.

In the past, I was able to get PCSX2 working in amd64 (probably in Karmic) using a 32-bit chroot but it gave me a migraine and I never want to relive that nightmare again.

It didn't run very well; games played at ~30fps with horrible graphical errors, but it ran.

Since then I have upgraded my hardware considerably.

Any ideas? Is there a debug mode?

---

