---
title: "Un-used swap"
date: 2010-05-27
forum: Desktop Environments
---

### Post by kammce on 2010-05-27
I am just wondering why KDE never uses my swap. On the KsysGuard, It reports that I have a GB of swap that is never used. I have 2GB of ram. This is only an issue because VMware will take up half of my computers resources for itself if, in the event, it needs to use it. How do I change this so my swap is being used.

I have:
Kubuntu 8.04LTS

---

### Post by Ranko Kohime on 2010-05-27
If you're not experiencing performance problems, then it's a good thing that your computer is not using any swap.

It's unusual, in my experience not to use any swap when running a virtual machine, but it's not automatically a bad sign if you're not.  It's actually quite normal not to use swap until the physical memory is nearly full with ACTIVE data.  The command line "top" program reports physical usage with INACTIVE included, and INACTIVE can be dumped at any time, without paging to disk.  It's also a lot faster if it does NOT get paged out to disk.

My laptop only has 1GB of RAM, and I don't even have a swap partition on the hard drive, because it's so small (EeePC with 8GB SSD).  Running the FULL 10.04 desktop version, with Firefox, Guitar Pro 6, OpenOffice.org and the terminal as well as other things open simultaneously, I still cannot get it to use over 75% of physical memory.

If you really must have more swap usage, you can try increasing swappiness.  [See this thread here.]("http://ubuntuforums.org/showthread.php?t=856485")  Just increase the number to something high, like 70-80-90-100.  But keep in mind that this will probably hurt your performance rather than helping it.

---

### Post by kammce on 2010-05-27
Thanks man. Now I understand how swap works on KUbuntu. I will try out your site and see if it works.

---

