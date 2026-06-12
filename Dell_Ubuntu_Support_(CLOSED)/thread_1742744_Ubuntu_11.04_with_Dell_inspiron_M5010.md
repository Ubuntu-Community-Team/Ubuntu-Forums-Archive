---
title: "Ubuntu 11.04 with Dell inspiron M5010"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by netyciukas on 2011-04-29
I have recently updated ubuntu from 10.10 to 11.04 on my Dell inspiron M5010 laptop. The problem is that ubuntu became incredibly slow. For example during installation files were copied in few minutes but system was configuring like 1.5 hour. Also I am able to start ubuntu after isntallation but it takes up to 10 minutes to boot to desktop. All commands in terminal take a lot of time etc. I tried disabling/enabling bios options but there was no use. I guess that the new kernel may be th issue.

Any ideas?

---

### Post by mörgæs on 2011-04-29
A slow installation is just because the servers are overloaded. Always wait a couple of months before installing a new release.

The best cure for a slow system (being fast in 10.10) is a fresh install.

---

### Post by Aaddron on 2011-04-29
I've used 11.04 on that model around Alpha 3 maybe Beta 1 and it ran great so it's probably an issue with the upgrade.

---

### Post by netyciukas on 2011-04-30
Tried doing fresh install, the results were the same. I also have windows 7 in other partition. Can this affect installation?

---

### Post by Novacaptain on 2011-04-30
I have the experience that ubuntu boots slower on my dell studio when I am using the proprietary ATI drivers.

---

### Post by netyciukas on 2011-05-03
I solved the problem. After a bit of investigation I noticed an "Disabling irq #18" error while booting. I had to disable acpi in boot options. Not it works well

---

### Post by mörgæs on 2011-05-03
Good, please mark the thread 'solved'.

---

### Post by JCSalomon on 2011-05-17
> **netyciukas said:**
> I solved the problem. After a bit of investigation I noticed an "Disabling irq #18" error while booting. I had to disable acpi in boot options. Not it works well

I’ve been having the same issue.  Disabling ACPI makes the system work at a normal speed, but it means the system cannot turn itself off!  Not sure how that qualifies as “works well”.

---

### Post by netyciukas on 2011-05-18
True, also battery widget doesn't show any information O.o but at least I can normally use the system

---

### Post by cnaguy on 2011-05-18
I have a Dell D420 and I am having an issue with Unity just running slow in general. Any program I click on takes awhile to load, especially LibreOffice. I think I may only have 512 MB of RAM but I would hate to upgrade to 2 gigs if I get the same results. Any ideas on this?

---

### Post by mörgæs on 2011-05-19
At the boot screen. you can select the classic Gnome desktop. Is it faster? 

Running **top** in the background while doing your normal work will tell you which application is heavy on the CPU.


You could also try to install the XFCE desktop environment, which will give you the option of booting into a Xubuntu system.

---

### Post by netyciukas on 2011-05-19
512 ram are enough. I also have old hp with 512mb ram and it works as a charm. Do you get "Disabling irq #18" error on startup?

---

### Post by theremper on 2011-05-27
I know this is marked as solved but an other problem has been brought up not being able to shut down using the acpi=off during boot. the solution is to use pci=noacp. fixes the problem straight away

---

### Post by netyciukas on 2011-05-28
Thanks a lot :) now everything works well

---

