---
title: "What is spinning my HD?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by Sushi on 2005-07-27
I have an old Compaq Armada 3500 laptop which used to run Gentoo. But since compiling took ages on that machine, I decided to try out Kubuntu on it. Now, the HD on that machine is pretty loud, and I want it to not spin all the time. And on Gentoo it did not spin all the time. It was pleasant to type away on a machine which was completely silent. But on Kubuntu the HD spins all the time. First I told it to spin down after 30 seconds on inactivity. But then the HD never spinned down. Then I reduced the inactivity-time to 15 seconds, and now the HD does spin down. For about three seconds, then it spins back up again.

How could I try to make the HD silent?

---

### Post by Shiven on 2005-07-27
have you got dma enabled by default on /dev/hda? 

dma will increase the amount of data being lifted off the the harddrive, but it will be lifted off at 15-20x faster than without it, thus making the harddrive not spin as often...

more or less a guess, but we have to start somewhere ^-^

incidentally, i'm a gentoo convert too :P

---

### Post by Sushi on 2005-07-27
[QUOTE=Shiven]have you got dma enabled by default on /dev/hda?[/quote]

Yes. 

> incidentally, i'm a gentoo convert too :P

I'm not a convert really. That machine wasn't ideal for running Gentoo, and I wanted to test another distro besides Gentoo. I have also tested Fedora Core 3 on that machine. And since (K)Ubuntu seems to be the new darling of the distro-land, I decided to check out what it has to offer. But my main machine is still Gentoo-only :).

---

### Post by PhilippWollermann on 2005-07-27
You could try to use some tool like "lsof" to see, if there are any open files, which are likely to be written into. Also you could watch the logfiles.. maybe Kubuntu is more verbose in logging than Gentoo and I remember, that syslog flushes the logfiles very often, thus spinning up the harddrive.

I remember reading a description of the "laptop-mode", somewhere in the kernel sources (I guess /usr/src/linux/Documentation/laptop-mode.txt .. but I'm not at my Linux machine at the moment). There were some hints, if the harddisk spins up too often.

Philipp

---

### Post by Sushi on 2005-07-28
[QUOTE=PhilippWollermann]You could try to use some tool like "lsof" to see, if there are any open files, which are likely to be written into. Also you could watch the logfiles.. maybe Kubuntu is more verbose in logging than Gentoo and I remember, that syslog flushes the logfiles very often, thus spinning up the harddrive.

I remember reading a description of the "laptop-mode", somewhere in the kernel sources (I guess /usr/src/linux/Documentation/laptop-mode.txt .. but I'm not at my Linux machine at the moment). There were some hints, if the harddisk spins up too often.

Philipp[/QUOTE]

Thank you for your reply, I'll look in to those :)

EDIT: I'm happy to report that enabling laptop-mode fixed the problem (well, it does spin up now and then, but it's silent for 95% of the time). If you are running Ubuntu on a laptop, you REALLY should use the laptop-mode!

---

### Post by noobuntu on 2005-07-28
How do you run in laptop mode?..i am using kubuntu on a laptop too and i ahve the same hdd probs u did

---

### Post by Sushi on 2005-07-29
[QUOTE=noobuntu]How do you run in laptop mode?..i am using kubuntu on a laptop too and i ahve the same hdd probs u did[/QUOTE]

Instuctions are for Debian, but they work in Ubuntu as well: [Link](http://www.xs4all.nl/~bsamwel/laptop_mode/tools/index.html)

---

### Post by coolclassic on 2005-07-29
Check your swap space you may be using this if memory size is small. This will cause the HD to constantly spin as Linux swaps files around.

---

### Post by mctavish on 2005-07-29
You could try adding the option 'noatime' to your fstab.  

I stole this from another thread:
> 
The noatime option is a good idea for any partition under linux. All it does is turn off the regular writing of file access times to the partition in question, a bit of info no application really uses and is generally gleaned from looking at timestamps anyway.

Thankyou dare2dreamer.

An extract of my /etc/fstab follows.

/dev/hdc4       /               ext3    defaults,noatime,errors=remount-ro 0       1

---

### Post by Bart Samwel on 2005-08-01
Note that [Laptop Mode Tools](http://www.xs4all.nl/~bsamwel/laptop_mode/tools), referenced earlier in this thread, automatically adds noatime to your mounts when laptop mode is activated, so if you're using that then there's absolutely no need to add it manually.

---

### Post by drizek on 2005-08-04
[QUOTE=Bart Samwel]Note that [Laptop Mode Tools](http://www.xs4all.nl/~bsamwel/laptop_mode/tools), referenced earlier in this thread, automatically adds noatime to your mounts when laptop mode is activated, so if you're using that then there's absolutely no need to add it manually.[/QUOTE]
 how can you check if dma is enabled? my hdd is VERY loud, buti could never get hdparm working(same problem as first post).

---

