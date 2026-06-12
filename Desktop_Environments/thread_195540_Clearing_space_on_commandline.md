---
title: "Clearing space on commandline"
date: 2006-06-13
forum: Desktop Environments
---

### Post by msandersen on 2006-06-13
I've got an old test machine, a Gateway, with these specs: 
498Mhz CPU
320Mb RAM
10Gb HD  
There's a 5Gb partition for Ubuntu, 3Gb for the system, 2Gb for Home. So it's tight. When I can afford it, I'll get a bigger hard drive for it.
I use it for experimenting with Linux mainly, as I don't trust it yet on my main machine, but want to keep XP around. It's made for Win 98, and doesn't run XP that well. Which makes it an interesting comparison machine with Linux on minimal hardware. Neither run particularly well on it. 

Previously in experimenting with Ubuntu Breezy, while installing stuff with Automatix, I ran out of space and got locked out of the graphical environment as a result. Some reading here resolved that one, by using "apt-get clean". Somehow deleting files in itself doesn't clear space I found. This left me with 300Mb.

I've taken the chance to upgrade to Dapper as I wanted to see how smooth it would be, using the Alternate CD someone got for me. I could clean-install, though it's a pain having to wait for Automatix to reinstall everything again. I didn't think there would be enough space, but tried anyway. I did have to restart configuring after using apt-get clean as I ran out of space, but it made it. Just. 8Mb to spare. Tempting my luck, I deleted some files and ran Automatix for some small things, but Dependencies saw it downloading more than anticipated (like, it seems, the Mozilla suite and a Java upgrade).

So, finding myself locked out again, and having cleaned the apt cache, I still can't start the graphical environment. Having read a bit about apt-get and dpkg hasn't helped much. How the hell people have managed to maintain their systems this way I don't know. I did manage to remove some packages with dpkg, but it has no effect on disk space, despite the packages being several Mb each.
And then there's Dependency Hell. One of the many things I experimented with on Breezy was GnuStep and WindowMaker. It was buggy as hell and pretty useless. It can go. But how on the commandline is the question. And the Mozilla suite. I don't need it.

But trying 
dpkg -P mozilla-suite
shows a library installed by AutoMatix (Flash-related I think) depend on it. Annoying.

Using dpkg -l gnustep*
gets me packages starting with gnustep. Trouble is, the list of packagenames is truncated to a certain length. So if the name is gnustep-base0.10, it only shows gnustep-base0. Which makes it useless for the remove command, which can't use wildcards.
Which is also where I run into the dependency problem:
A depends on B and C.
dpkg -r A B C
Complains that B can't be removed as D and E depend on it, and C has dependencies F and G, and so A can't be removed because A and B can't. And so on.

So, is there a way to remove all gnustep and Windowmaker-related files and its dependencies simply? Similarly with some KDE apps, they installed core KDE parts. Removed Krita, but the KDE dependencies remain. Would have liked KDE, but didn't have space.

I know; clean install is the easiest and cleanest, my home dir has anything I want to keep. But I want to learn how to clean house and get space back. Why it hasn't cleared even a few bytes already is beyond me, unless dpkg -r and rm doesn't really delete things. Not even man pages work in this state since they can't be unzipped.

---

### Post by msandersen on 2006-06-13
I red somewhere here that unimstalling old kernels can free up some 300-400Mb each. I've got about 3: -9 -10 and Dapper's -23.

---

### Post by msandersen on 2006-06-13
Well, with a bit of trial-and-error finally managed to remove one of the kernel images, after having figured the full name of the package:
```
sudo apt-get remove linux-image-2.6.12-9-686
```
It said it would free up about 70Mb. It at least cleared enough to start Gnome, but Administration->Disks showed only 17Mb freed. From here I could use Synaptic to clear unneeded packages. I removed mozilla-suite too, the dependency libswt was an opensource version of Swing for Java apparently.

---

