---
title: "bootsector problems"
date: 2009-05-10
forum: General Help
---

### Post by lala800 on 2009-05-10
hello all,

Im relatively new to linux (ubuntu), I had my computer dual booted with ubuntu & win XP, using grub as "boot manager".

my XP installation started to get really slow & I wanted to rearrange the partitions. so I decided to wipe the harddrive clean and reinstall everything.

I booted from the ubuntu live CD, used gparted to remove all the partitions and format the harddrive.

THE PROBLEM Im having is that it wont let me install windows now, I get the "NTLDR is missing" error message when trying.  All the solutions I have found so far are based on different ways to let you boot your windows OS, , , but I don't have any OS on the harddrive, its wiped clean. What to do? how can i restore/fix the bootsector??

Im however able to run ubuntu live CD & install ubuntu again, maybe something can be done from within ubuntu.

As I need to have windows installed for school Im almost at the point of buying a new harddrive, but thats seems rediculous, bootsector should be fixable somehow, 

help appreciated

---

### Post by logos34 on 2009-05-10
try erasing the MBR:
> 
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1

---

### Post by jimbob on 2009-05-10
I think you need to install XP first, telling it to use half (or whatever) of your drive and then install Ubuntu telling it to use the rest of the disk.

Clean off the drive completely again using Gparted but don't bother formatting - the installations will take care of that.  Start out with completely "unallocated space" and do XP first.

---

### Post by logos34 on 2009-05-10
> **jimbob said:**
> I think you need to install XP first

but he already tried that...error message

---

### Post by jimbob on 2009-05-10
If it can't find the NTLDR on the XP install CD then it must be the cd drive hardware or the CD itself is bad (fingerprints,ert ...).

---

### Post by logos34 on 2009-05-10
that makes sense...I was thinking maybe windows was detecting grub bootloader

---

### Post by lala800 on 2009-05-10
finally got it to work.  had to do "sudo dd if=/dev/zero of=/dev/sda bs=446 count=1" twice, didnt work the 1st time but the 2nd, weird.

nobelprize to logos34

btw i had previously tried running fixmbr from the win recovery console, that did nothing for me.


=D>

---

### Post by logos34 on 2009-05-10
> **lala800 said:**
> 
nobelprize to logos34

boy, I could sure use the check that comes with it!

yeah fixmbr should have overwritten it...xp just doesn't want to cooperate sometimes.

enjoy

---

