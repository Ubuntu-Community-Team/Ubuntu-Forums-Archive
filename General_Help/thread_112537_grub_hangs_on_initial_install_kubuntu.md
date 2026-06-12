---
title: "grub hangs on initial install kubuntu"
date: 2006-01-04
forum: General Help
---

### Post by woutervg on 2006-01-04
Hi, 

I was eager to try kubuntu (5.10) on my P4, since it works as a charm on my Toshiba Sattelite. However, I'm faced with a problem.

I have two disk, 80G & 15G (/dev/hda and /dev/hdb). I configure /dev/hda3 as my root partition, with the boot flag set. Home is on my other disk.
I tell GRUB to install on the MBR on the first disk, I remove the cd-rom and reboot. My computer reboots, and all I see is 'GRUB ' .... that's it... is hangs !?!?! No menu, no cursor, no response on any input. There is nothing I can do, but to press ctrl-alt-delete, and the same happens again.

What should I do?

I cannot get back into the install system, all my settings seem to have gone. So I am left woth going through the whole install fase again, and ending up with the same error.... Is there a way to rescue the install?

All suggestions are welcome!

Wouter

---

### Post by One Quick Question on 2006-01-04
If your computers have floppy drives, check out the **grub-disk** package on your Toshiba. If not, burn a live CD.
That will get you access to your hard drives.  As for correcting the problem...   That's beyond my experience.  If reinstalling GRUB doesn't do anything useful, I suppose you could check out LILO, as it is another boot loader.

Hopefully this helps a little.

---

### Post by merci on 2006-01-19
Hello Wouter,

have you solved the problem yet?
I'm in the totally similar situation but I tried lilo afte GRUB didn't work. Unfortunately in the phase of initial setup installing lilo it stopped on 50%. :confused: 

I have a Toshiba Tecra S2 installed WinXP on it and I'd like to install KUBUNTU in separated partition as well.

Every help is welcome,
thank you,
merci

---

### Post by ozorba on 2006-01-19
This problem normally happens when you have errors with your install CD. You need to ensure that the iso image md5 cheksum is correct and that your CD write process has not done anything funny.

I once downloaded the ISO image and wrote it with k3b. At the same time I was doing lots of things. k3b did not report any problems. When I tried to install Ubuntu I had lots of install problems...

---

### Post by merci on 2006-01-20
Hello,
the check sum is correct.
merci

---

