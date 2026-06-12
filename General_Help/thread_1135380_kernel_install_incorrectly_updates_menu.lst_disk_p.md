---
title: "kernel install incorrectly updates menu.lst disk partitions"
date: 2009-04-24
forum: General Help
---

### Post by garymansell on 2009-04-24
Hi,

I originally built my Ubuntu sytem spanning the whole drive so the menu.lst file specified the root disk partition as hd0,0

I have since moved the partition and installed Windows XP into partition hd0,0 so that the system will dual boot. The Ubuntu partition is now hd0,1

I update my menu.lst file so that all boot stanza's refer to the Ubuntu partition as hd0,1 and the machine is fine.

Unfortunately, whenever I upgrade the kernel it puts in a new menu.lst file and this again refers to the Ubuntu root as being hd0,0. I then have to go through the file and manually correct it.

It seems that the Ubuntu install must save the details of where it originally installed the OS and use this to populate menu.lst whenever a new kernel is added. How do I change this to prevent this annoyance occurring.

Thanks in advance for any help

Gary

---

### Post by sdennie on 2009-04-24
Actually, it's probably a grub configuration issue.  It's possible that just updating grub will be sufficient but, I'm not sure:

```

sudo update-grub

```

---

### Post by drs305 on 2009-04-24
Check the entries for "# kopt=" and "# groot=" in the middle section of menu.lst and make sure they correctly point to the correct partitions. 

These are in the *automagic* section of menu.lst so make sure you leave the single # symbol at the start of the line. You have edited menu.lst before so I won't go into the details of how edit the file.

---

### Post by garymansell on 2009-04-27
The groot option looks like it should do the job - thanks very much.

This has been annoying me for some time now.

Rgds

Gary

---

