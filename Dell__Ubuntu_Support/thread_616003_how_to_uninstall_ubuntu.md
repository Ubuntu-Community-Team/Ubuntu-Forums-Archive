---
title: "how to uninstall ubuntu"
date: 2007-11-17
forum: Dell  Ubuntu Support
---

### Post by falconsdive on 2007-11-17
I've been having problems with my update manager and cant seem to get it fixed.  So, since I have the Instalation CD and my files are backed up, I wanted to wipe my whole hard drive and remove ubuntu so that I can reinstall the O.S.  Can I do it?

---

### Post by schauerlich on 2007-11-17
Just tell it to format the partition in the installer.

---

### Post by falconsdive on 2007-11-17
huh?!

---

### Post by shad0w_walker on 2007-11-17
There is an option in the installer to delete the partitions on your hard drive and make a new one to install to.

---

### Post by falconsdive on 2007-11-17
ubuntu is the only O.S. that is on my computer.  If you could give me a step by step process on how to do this, i would really apreciate it.

---

### Post by mellowd on 2007-11-17
boot off the CD. When you get to the part where it asks you about partitions tell it to use the entire disk. It will then format it for you which means everything that was there will be gone

---

### Post by sciurus on 2007-11-19
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by cprofitt on 2007-11-20
> **falconsdive said:**
> ubuntu is the only O.S. that is on my computer.  If you could give me a step by step process on how to do this, i would really apreciate it.

Boot with the live CD.

Run the install.

Select the option to use the entire disk (which will format the disk).

If really want to be sure you can use gparted from the live CD and wipe the partitions manually.

I personally would install with a sep. partition for your /home

---

### Post by Sims2789 on 2007-11-20
> **indigo196 said:**
> Boot with the live CD.

Run the install.

Select the option to use the entire disk (which will format the disk).

If really want to be sure you can use gparted from the live CD and wipe the partitions manually.

I personally would install with a sep. partition for your /home

Or just have one giant one (and one gig of swap) so that you don't run into space allocation issues.

---

### Post by falconsdive on 2007-11-21
when i boot from the cd and select "start or install" i get this error:

    /bin/sh: can't access tty; job control turned off

what does this mean?

---

### Post by sciurus on 2007-11-24
> **falconsdive said:**
> when i boot from the cd and select "start or install" i get this error:

    /bin/sh: can't access tty; job control turned off

what does this mean?

Is the cd for 7.04 or 7.10? If 4, try 10. If still no good, try the alternate instead of live cd.

---

### Post by gbrainin on 2007-11-24
I just saw a solution for this curious problem.  In brief, you need to add an option ("irqpoll") to the boot line.  Details, explanation, and references here:

[http://ubuntuforums.org/showpost.php?p=3822460&postcount=4]("http://ubuntuforums.org/showpost.php?p=3822460&postcount=4")

---

