---
title: "Kubuntu HDD clogged"
date: 2006-08-10
forum: Desktop Environments
---

### Post by casperlingus on 2006-08-10
I'm sure this has a straightforward answer.  I am running kubuntu on my laptop, and left Neverball running all night.  When I returned, it required a hard reboot and wasn't able to log in.  After booting into recovery mode I notice that all 16GB of my primary partition is full.  

I'm gonna take a guess that there's a memory leak in Neverball, and perhaps the memory leak inspired my computer to start writing garbage to the HDD that it couldn't delete when I had to hard reboot.

Currently, a *df -h* indicates that all 16GB are used.  When I boot into a live session with the CD, mount the HDD, and get properties on the mounted filesystem, it counts up everything and claims only 7GB are used.   

I'd happily delete what I need to...if I could find it.

Casper...

---

### Post by casperlingus on 2006-08-10
Bump.

I use this computer for work, I really need to figure this out.  I can't imagine it's that hard.

I have only been able to locate 7GB of files, but it claims all 16GB are full.  Where could the extra data be hiding?

---

