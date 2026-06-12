---
title: "A few questions..."
date: 2009-02-27
forum: General Help
---

### Post by cwortman on 2009-02-27
I really love Ubuntu, but there are a few things that bother me a little.

Ubuntu 8.10
How do I speed things up? I am not afraid of getting my hands dirty and breaking things for the sake of learning. I just want to have fun here. 

Will 9.04 be faster?

Why hasn't ext4 been included as even an option until now?

What are some amazing applications?
-fruity loops/garage band replacement
-language learning software like rosetta stone or byki
-absolutely anything else I could install and play with and have fun with

Is there a way to speed up flash 10?
-Hulu and YouTube are really laggy compared to Windows or OSX

Perhaps the flash isn't my issue because when using the NVidia recommended drivers so I will try and use the other driver. I seem to have graphical glitches when using desktop effects, like it will cause the frame to get all messed up. It is a NVidia 7300LE 256(512 shared support). All my hardware is tested and good, and works awesome with XP, Vista, 7, and osx86(I actually own a Mac Mini and just wanted to play, and osx86 is long since removed). I have done multiple hardware tests using programs to test them and it all comes back with positive results.

Help with the graphical issues would be heavily appreciated as that is my top priority atm.

No I won't use another distribution I am about solidarity and think only 1 or 2 distributions should be commercially supported. Sure the rest of the distributions can co-exist for specialties, but I am against the inane 600 different iterations of the same thing. I refuse to use mint, ultimate, ubuntu studio. All of these are a good examples of what I mean. I get why they exist, someone has a different idea of how it should be done. Honestly, though, most people are used to solidarity and prefer it that way. I think that, honestly, we should push Ubuntu (have the rest of them exist) but only have Ubuntu and another desktop distribution, and at tops 3 desktop distributions pushed. I am all for having just Ubuntu in the lime light. It doesn't mean the rest of them can't exist. I am sure there is a better one suited for my needs, but I think Ubuntu CAN fit all my needs.

---

### Post by Ms_Angel_D on 2009-02-27
> **cwortman said:**
> works awesome with XP, Vista, 7, and osx86(I actually own a Mac Mini and just wanted to play, and osx86 is long since removed). I have done multiple hardware tests using programs to test them and it all comes back with positive results.

Just remember that just because hardware works great with Windows doesn't mean it will also be the case with Linux, that being said good luck with getting your kinks worked out.

If you want software, just open add/remove programs there are a ton of "toys" in there for you to mess with ;).

---

### Post by oldos2er on 2009-02-27
Look at the Tips & Tutorials subforum, there are many posts there about speeding up Ubuntu.

 ext4 is in the 2.6.28.x kernel, available in Jaunty (9.04).

 Synaptic Package Manager can search the repositories for any type of program you wish to install.

---

### Post by cwortman on 2009-02-27
OSX86 just happens to be BSD with OpenDarwin underpinnings. Sure aqua works and all but it uses the OpenDarwin driver system. If you use BSD and OpenDarwin you use kext based drivers. I just tried it out and it works absolutely perfectly with the NVidia darwin drivers without an issue. I didn't use the freeBSD kernel, because the drivers are not supported there yet. 

I tried the older NVidia drivers for Ubuntu and they didn't fix it and made flash even slower and made desktop effects just crash Xorg. Is there something I am missing? Is NVidia actively trying to cripple Linux for some reason?

Add/Remove doesn't contain enough information and it seems a mess. I would really like to know some awesome applications to make Ubuntu shine. What makes Ubuntu special to you; what applications can I get in Ubuntu to make it special to me? Sure there is Open Office, Gnome, Pidgin, and Firefox, but what else exists that gets an 11/10 to you that makes Ubuntu amazing?

---

### Post by mb_webguy on 2009-02-27
I wouldn't suggest going to 9.04 quite yet, since it hasn't been released yet.  You're bound to encounter bugs that haven't been worked out yet.

One way you can speed up Ubuntu is to use a lighter desktop environment than Gnome (such as Xfce, which you can get by installing the xubuntu-desktop package), or go for a windows manager like Openbox and drop the desktop environment entirely.  I'm using Openbox with PyPanel right now, and it's pretty swift.

[Here]("http://ubuntuforums.org/showpost.php?p=6630710&postcount=7") are other things you can do to speed up your system a bit.

If you're a true speed freak, you could try [compiling your own kernel]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by BOOBOOJS on 2009-02-27
I have tried a lot of Linux Distros and have allways come back to Ubuntu for many reasons. Here are the 3 main things that I love about ubuntu:
1. Synaptic is by far the best package manager I have seen
2. Ubuntu has a huge community to answer questions in this forum
3. Ubuntu is more user friendly, I love the tech side of Linux but don't have time to compile every app I want etc.

My fav apps in ubuntu are:
GAMES:
neverball and neverputt -- minature golf, labyrinth 
supertux -- mario clone
atanks -- Scorched Earth clone
penguin-command

MULTIMEDIA:
kino -- video editing
k9copy -- dvd copy
k3b -- CD/DVD burning
ubuntu-restricted-extras -- installs codecs, flash, and java

OFFICE
gnucash -- cross platform ms money or quicken replacement
openoffice -- office replacement
bitpim -- sync data to and from your phone with a data cable

GENERAL
truecrypt (opensource cross-platform encryption -- download from truecrypt.org  
acetoneiso2 -- mounts cdrom image files (pain to get working under amd_64 but doable)
virtualbox -- free vmware
keepassx -- cross platform password manager

Those are just a few of mine. I'm sure others could tell you about more

---

### Post by cwortman on 2009-02-28
Yes I took and went back to KDE using 4.2. I compiled my own kernel and just installed lotsa stuff. I am having a much better time here. Thank you.:KS

---

### Post by cjwatson on 2009-02-28
We didn't include ext4 until now since it wasn't declared stable upstream until just before 8.10 released (too late to do anything about it). We prefer to minimise the number of times we're told that one of our stable releases ate somebody's filesystem. :-)

(Not a theoretical concern even now; there have been serious bugs reported against ext4 that are still being worked through.)

---

### Post by cwortman on 2009-03-01
Wow I have been using ext4 for about 6 months without an issue. I use it on an SSD drive and it works amazingly. I had no idea there were bugs thank you

---

### Post by cjwatson on 2009-03-01
I should back up my statement: I was referring to [bug 317781]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781").

---

### Post by Xiong Chiamiov on 2009-03-01
> **BOOBOOJS said:**
> 
1. Synaptic is by far the best package manager I have seen

You have apparently never used [pacman](http://wiki.archlinux.org/index.php/Pacman) and [its](http://wiki.archlinux.org/index.php/Yaourt) [wrappers](http://xyne.archlinux.ca/info/powerpill).

---

### Post by cwortman on 2009-03-01
I see the bug. I then went on to compile the AMD64 kernel. It has no issues with my 32 bit kernel, however the problem exists only with AMD64. I was on and turned off the surge protector to re-enact it. The 32 bit kernel ran a file check and everything was fine, however the 64 bit kernel seems to have issues. The 64 bit stuff in Linux all seems a bit shaky to me anyhow, so I only stick to 32. Plus 32 is easier to code for. I don't see any actual gain from coding for 64 other than perpetual speed and segfaults seem to be protected and doesn't take everything out. But I debug things and have rare instances with any real segfaults anymore. When you come to brass tacks and actual speed that you perceive, 64 bit offers nothing. Perpetual speed only seems to be good for 3D graphics, however with my sli 2xNVidia 8800 GT cards, I see no added gain in graphics. On my gaming rig I have Vista sp1 32 and 64, 24Gig ram, 2xNvidia 8800GT, AMD FX60. When I run 32 and 64 I see no gain there either unless I am running photoshop cs4.

---

