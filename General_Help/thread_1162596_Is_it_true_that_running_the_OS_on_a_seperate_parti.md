---
title: "Is it true that running the OS on a seperate partition lets you swap distros?"
date: 2009-05-17
forum: General Help
---

### Post by w.g.hanna on 2009-05-17
Well - its getting time to update.  Hardy Heron was my first linux and while i had fun learning it - i made some mistakes along the way.  I'm about to back up my hard drive, and do a total reinstall with the latest Ubuntu.  Is it true that if I devote a partition to the OS and a separate partition for the data that I can swap distros without risking data loss?  

Also - I'm running 32 bit right now because, at the time, i was told that wine and flash didn't run in 64 bit.  i've heard that flash runs on the 64 bit version.  how about wine?

---

### Post by Dr.Vista on 2009-05-17
> **w.g.hanna said:**
> Well - its getting time to update.  Hardy Heron was my first linux and while i had fun learning it - i made some mistakes along the way.  I'm about to back up my hard drive, and do a total reinstall with the latest Ubuntu.  Is it true that if I devote a partition to the OS and a separate partition for the data that I can swap distros without risking data loss?  

Also - I'm running 32 bit right now because, at the time, i was told that wine and flash didn't run in 64 bit.  i've heard that flash runs on the 64 bit version.  how about wine?
I believe that's right. I'm not pretty sure but I think thats possible.

---

### Post by mjitkop on 2009-05-17
Yes, if you have separate partitions for the OS and your home folder, you can install a new version of Ubuntu over your OS partition and your home partition will be untouched. Just be careful during the installation of the new OS not to format your home partition, of course.

That said, some profile data used by applications get saved in your home partition so this might cause problems after you reinstall your applications (packages). I suggest before you reinstall your packages that you delete the profile data files that are in your home partition. Those profile data files usually start with a . (dot) followed by the name of the application. For example: .firefox. Hopefully somebody else will confirm this or correct me if I'm wrong.

I can't anser about 64-bit functionality.

---

### Post by Aearenda on 2009-05-17
In many cases, the profile data will be upgraded or still work - I wouldn't just wipe it all out.

What I do is keep a separate partition for all my folders that I want to keep, and link these into my home folder, but I have a home folder in the root partition for each OS I want to keep. And I have each OS in a separate partition, of course. At the moment, my main laptop has this setup:

/dev/sda1 = root partition for Jaunty
/dev/sda2 = root partition for Intrepid
/dev/sda3 = swap
/dev/sda4 = partition for permanent folders

The icons in my home directory as seen in Nautilus show that they are links, but otherwise function normally. 

This allows me to revert easily if a new release doesn't work well at first. I had to do this a lot with Intrepid (back to Hardy), but Jaunty was right first time.

---

### Post by mb_webguy on 2009-05-17
Re: the bit about 64-bit...  64-bit Linux is very well supported.  Even if an application doesn't run natively in 64-bit, you can install the 32-bit version.  Flash and Wine run just fine on my 64-bit system.  Actually, Flash runs better on my 64-bit system than on my 32-bit system.

---

### Post by jms1989 on 2009-05-18
> **mb_webguy said:**
> Re: the bit about 64-bit...  64-bit Linux is very well supported.  Even if an application doesn't run natively in 64-bit, you can install the 32-bit version.  Flash and Wine run just fine on my 64-bit system.  Actually, Flash runs better on my 64-bit system than on my 32-bit system.

I must ask, how did you get flash to run better on the 64bit version then on the 32bit version? I have flash working on ubuntu 64bit but its a bit flaky. Like when I try to do anything on sites that use flash, the browser window will quit responding for a little bit.

To answer the op's question, its very well possible to dual boot distros that have either a separate home partition or independent one. I actually have a 32bit and 64bit version of ubuntu 8.10 install onto separate partitions on my computer and they both share the same home partition.

Flash works to an extent on the 64bit version from what I can tell and wine works without a hitch. :)

---

### Post by mb_webguy on 2009-05-18
> **jms1989 said:**
> I must ask, how did you get flash to run better on the 64bit version then on the 32bit version? I have flash working on ubuntu 64bit but its a bit flaky. Like when I try to do anything on sites that use flash, the browser window will quit responding for a little bit.

I uninstalled all of the Flash plugins from the repos, and deleted any lingering related files.  Then I downloaded the official 64-bit Linux Flash plugin from Adobe and dropped it into the /usr/lib/mozilla/plugins/ directory.  Works like a charm.

---

### Post by dcstar on 2009-05-18
> **jms1989 said:**
> 
.........
To answer the op's question, its very well possible to dual boot distros that have either a separate home partition or independent one. I actually have a 32bit and 64bit version of ubuntu 8.10 install onto separate partitions on my computer and they both share the same home partition.


The **same** version of Gnome/KDE can be shared across different distros, but you **cannot** share a /home across different versions without the risk of major problems.

---

### Post by louieb on 2009-05-18
> **Aearenda said:**
> ... At the moment, my main laptop has this setup:

/dev/sda1 = root partition for Jaunty
/dev/sda2 = root partition for Intrepid
/dev/sda3 = swap
/dev/sda4 = partition for permanent folders
...


Have used a separate /home partition in the past. But changed to this setup when I got a bigger hard drive. Works well.):P

---

### Post by detroit/zero on 2009-05-22
> **dcstar said:**
> The **same** version of Gnome/KDE can be shared across different distros, but you **cannot** share a /home across different versions without the risk of major problems.
I've had the same home directory on the same laptop since the days of Feisty and I've never had a single problem.

Just saying..

---

