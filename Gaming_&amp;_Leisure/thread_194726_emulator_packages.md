---
title: "emulator packages"
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by stairwayoflight on 2006-06-11
hey,

in another version (breezy?) of ubuntu i though xmess zsnes and xmame were available in the repos. are the packaged versions broken for 6.06?

---

### Post by Zelut on 2006-06-11
I just did a search for xmess and xmane and found them.  Might want to make sure you've got the right repositories enabled and try searching again in Synaptic.  Take a look [here for updating the repos]("https://wiki.ubuntu.com/AddingRepositoriesHowto") if you need.

---

### Post by leech on 2006-06-12
Xmame/Xmess is in Dapper, in the Multiverse repositories, unfortunately the versions are quite old (0.101) whereas the Debian Sid packages are quite a bit newer (0.105).  The latest release of Xmame is 0.106.

Leech

---

### Post by stairwayoflight on 2006-06-14
hmm.. i updated my repos' according to the main link from the ubuntu.com site.. clicking on "support" "doc home" and "desktop" i think.. but it just said to click on "software management" then check all the boxes for available repos. thats just what i did.

now i ran automatix, and it said it was "restoring my sources.list" to the original.. i'll post it here to see if its right??

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## from the Automatix install forum guide
deb http://www.getautomatix.com/apt dapper main

```

---

### Post by Perfect Storm on 2006-06-14
I wrote a howto compile the latest ScummVM if you're interested: 
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=33&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=33&Itemid=63)

and the latest Dosbox:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=23&Itemid=63)

---

### Post by stairwayoflight on 2006-06-14
so you're saying the debian package is compatible with my dapper 6.06 i386 install? how do i know if binary compatibility isn't broken?

ok and while we're on xmame, i realized sound was screwed and had to max out the buffer sliders in gxmame. right now i installed xmame .86 bin's i found somewhere. 2 more things i need help on..

1 - how do i know my mame roms are compatible with my version of xmame?? i sometimes get missing files.

2 - right now 3d, xorg 7.0, and my kernel are working. i could download the latest kernel source for my athlon-xp, and through 'make menuconfig' enable preemption in the kernel, and that would speed up games, i/o, audio?? but i don't know how to be sure my video (savage) and 3d etc. would all work after or could be easily restored.

---

