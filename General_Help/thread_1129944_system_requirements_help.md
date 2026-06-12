---
title: "system requirements help"
date: 2009-04-19
forum: General Help
---

### Post by 123456789123456789123456 on 2009-04-19
This is a little confusing for me, usually when I am dealing with ubuntu and xubuntu, most of the computers had for ubuntu more than 512mb ram, and xubuntu more than or at 256mb ram.  I am redoing a computer, it currently has only 256mb ram, and will have another 256mb chip.  The motherboard has a built in video card, so I assume some of the system memory would be used as shared graphics memory, considering the age of the computer, I would guess no more than 64mb, possibly max of 128mb.  I understand from the section of the ubuntu.com web site, that alternate install requires 256mb ram, where as the live installer requires at least 384mb.  However once the system is installed on the hard drive, does the system require 256mb ram, or 384?  Logically considering how live cd's work, I would say that 384 would be a bit high.  Since the live cd has to load everything, from the desktop, live user GUI, and the installer main data.  but once the system is on the hard disk, all of this information is not needed to be placed in ram.  can someone help relieve this confusion.

---

### Post by 3Miro on 2009-04-19
What exactly is the question?

Ubuntu and Xubuntu would run with fewer resources than listed, however, they will have to resort to swap and the system would be slow and possibly not as stable.

The Linux kernel and the basic processes take almost no memory. It is the graphical environment (GNOME/Xfe/KDE) and the applications that take up the RAM. Xfe would take less than the others. If it is still too much, try installing a even smaller desktop (window maker perhaps).

---

### Post by 123456789123456789123456 on 2009-04-19
I guess what I am asking then is how well will Ubuntu 8.10 and soon to be 9.04 run on a computer with a intel processor, and 512mb-64mb ram.  The minus 64mb for video shared memory.

---

### Post by s.fox on 2009-04-19
Hi,

[Here]("https://help.ubuntu.com/community/Installation/SystemRequirements") is a link to the minimum system specifications for Intrepid Ibex.

Hope this helps.

-Ash R

---

### Post by 123456789123456789123456 on 2009-04-19
Thanks that is exacltly what I needed.  knowing that information, even if the shared memory for some reason was 128mb, which would be barely good for vista, that would leave 384mb ram for ubuntu, which it should run on fine.  the biggest concern that the customer has is speed.  I know I managed to get xubuntu running on a computer with only 184mb useable system memory, where it has 192mb physical ram.  It runs on that machine, all be it a bit slow at times, it runs effectively.

---

### Post by paradigm2 on 2009-04-19
> **123456789123456789123456 said:**
> I guess what I am asking then is how well will Ubuntu 8.10 and soon to be 9.04 run on a computer with a intel processor, and 512mb-64mb ram.  The minus 64mb for video shared memory.

What is the processor speed?  I have one (Ubuntu Jaunty beta) which is 750 Mhz and it is a bit slow with like 650MB of RAM ( but 128MB is used for shared video).  The biggest thing bogging it down seems to be the processor.  It is still functional but if I open more than four Firefox tabs or so it starts to slow considerably.  Xubuntu probably would have been a better choice for this machine of mine.

---

### Post by 123456789123456789123456 on 2009-04-19
for one thing, Jaunty beta is just that a beta version, it probably has not yet had all bugs worked out yet, that may be different when it is released in 4 to 5 days.  From what I can gather from dell, the processor should be 1.2 to possible 2ghz at the most, intel celeron processor, cerca 2002,2003

---

### Post by Gen2ly on 2009-04-19
I got Gnome 2.22 on an old 350Mx mac with 192MB of RAM and it runs ok enough to work with.  Gnome 2.26 isn't going to me much different than that.  To really have it run well though you should be just fine with 512Mb of RAM.

On a sidenote:  A bit surprised the alternate install takes 256 of RAM.  Honestly that seems way to much for pretty much a text based installer.  I've installed Gentoo and Arch on the mac and they did just fine with that amount of RAM.

---

### Post by 123456789123456789123456 on 2009-04-19
the alternat installers as far as I understand how boot cd's work, loads more than just the graphical interface to use.  the 256mb ram probably refers to all the features that it loads into memory, possible installation programs and files, so that it won't have to look on the cd for all the files.  If they made it look on the cd, load the files to ram, take from ram to hard disk, like windows installers do, the install process would take a whole lot longer than the normal 25 min approx.

---

### Post by Gen2ly on 2009-04-20
Good point.  There is a certian amount of caching going on: kernel, file system structor, core utils, and the installation program programs that maybe i didn't thing about.  Just surprised mereally as it probably doesn't need to be that high.  But, i guess, as computers improve, requirements go up, plus, i imagine, that number is a bit conservation.

---

