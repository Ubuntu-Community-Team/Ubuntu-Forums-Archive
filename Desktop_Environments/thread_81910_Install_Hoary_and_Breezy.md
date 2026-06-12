---
title: "Install Hoary and Breezy?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by oghanchi on 2005-10-25
Hello everyone:

I am a long time reader and occasional poster, but this is my first ever question post....

Here is my situation:

I had Ubuntu hoary installed on a hard drive, which I took out and replaced it with a new harddrive. 

I installed Breezy on the new hard drive, which is now functioning without any problems.

I now want to add my old hoary drive as a slave and add hoary into the breezy grub. Here is what my partitions look like:

Breezy:
/dev/hda1 = boot 
/dev/hda2 = root
/dev/hda3 = swap
/dev/hda4 = home

hoary: (when hoary was installed this drive was hda)
/dev/hdb1 = boot
/dev/hdb2 = root
/dev/hdb3 = swap
/dev/hdb4 = home

When I added the hoary drive as a slave, I changed the hda's to hdb's in /dev/hdb2/etc/fstab to reflect the fact that the drive is now hdb.

I also edited the breezy grub to add the hoary install. I am able to boot, but am unable to get X working in hoary. It gets me to runlevel 3, but with some errors during the boot process, which go by very quickly, and I can not read them. It also shows the OS as "Breezy" and not "Hoary" at the prompt. I can log in using a user account, but X does not start.

X starts and works perfectly in breezy, however. 

My questions: Is there anyway this could work, without reinstalling hoary all together? 
If yes, what am I missing?

Thanks in advance!

---

### Post by oghanchi on 2005-10-25
anyone?

---

### Post by manicka on 2005-10-25
can you post your fstab?

---

