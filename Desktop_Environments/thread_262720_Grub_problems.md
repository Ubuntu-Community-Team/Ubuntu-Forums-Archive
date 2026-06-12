---
title: "Grub problems"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Old Pink on 2006-09-22
I get grub error 22 when booting, as I removed one of my ubuntu partitions.

How can I remedy this from livecd? I figure I need to mount hda2 or install grub on it's own from LiveCD?

How do I do either of the above? 

ANSWER ASAP PLEASE, I NEED THIS COMPUTER

---

### Post by dom on 2006-09-22
well, Error 22: No such partition., that should be handy to fix

if you are familiar with the shell, i would try opening one, 
going to the boot partition, 
copying menu.lst to menu.lst.original - in case you mess up completely :)
edit menu.lst and remove any references to the removed partition.

i'm assuming the removed partition wasn't something important, and you have some bootable partitions left :)

there may well be a quicker way, such as telling grub to set itself up from scratch again.

---

### Post by ghettobilly on 2006-09-22
run livecd after its up ctrl+alt+F1 for terminal

sudo mount /dev/hd(whatever yor partition is) /media
sudo chroot /media
update-grub
exit
then reboot

have used this method few times after changing harddrives

---

### Post by Herman on 2006-09-22
Yes, or, if you have the latest [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), just boot that and select 'English Super Grub Disk'-->Gnu/Linux --> Fix Boot of Gnu.Linux (Grub).

Regards, Herman :D

---

### Post by anaconda on 2006-09-22
It sounds that you destroyed the partition, where grub stage2 was. So now your grub doesnt work, becayse most of it doesn't exist anymore.

You should install new grub, or lilo or some other boot manager.

I havent used lilo, but it fits completely to mbr, and doesnt need anything from your ubuntu partition.

I solved a similar problem by installing a small linux distribution  "DamnSmallLinux =50MB" to work as a "boot manager" or rather a sepatrate boot partition... Now as long as I dont delete my DSL partition I can boot to any system I want..

---

### Post by Old Pink on 2006-09-22
Thank you all for your replies! :D 

I'll try and get it fixed when I get home. :razz: 

> **anaconda said:**
> You should install new grub, or lilo or some other boot manager.

How exactly do I do that, considering my situation?

---

### Post by Old Pink on 2006-09-22
None of the above suggestions worked. :(

---

### Post by Old Pink on 2006-09-22
I did fixmbr and now "operating system not found" HELP!!

---

### Post by Herman on 2006-09-22
What output do you get from the 'sudo fdisk -lu' command when running from a Live CD? Please post that here if you want specific help. ```
sudo fdisk -lu
``` Or, if it's easier for you, a screenshot from GParted ('System'-->'Administration'-->'Gnome Partition Editor', will be very good instead.
Perhaps your partition numbers have been switched around on you somehow without you knowing, that could cause some complications, but nothing you can't recover from.

For booting Linux in an emergency, Super Grub Disk is about the most heavy duty and feature-packed software around. It will also boot Windows for you in most cases. [Super Grub Disk Documentation Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

To boot WIndows in an emergency, the best thing to do is make your self a Windows boot disk with NTLDR, NTDETECT, and boot.ini on it. You can even edit boot.ini on the boot floppy as many times as you like in case the problem is caused by partition numbers being changed. For how to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/")

If nothing works, maybe your partition table in your MBR is corrupted somehow, GParted or sudo fdisk -lu will tell us if it is or not, or help us get the correct partition numbers of that's all it is that's wrong. If your partition table is damaged, you may need to search for software that can fix that. We'll cross that bridge if we get to it.

Regards, Herman :D

---

