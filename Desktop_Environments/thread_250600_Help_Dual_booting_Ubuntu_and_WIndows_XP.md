---
title: "Help Dual booting Ubuntu and WIndows XP"
date: 2006-09-04
forum: Desktop Environments
---

### Post by frequenicity on 2006-09-04
A little background:
I have installed Ubuntu on a clean HD that is dedicated to linux and seperate from my Windows drive. I have this on the primary channel of IDE1. My Windows drive is on the slave channel of IDE1. Here is a copy of my menu.lst(the important parts):

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I have tried adding:
> title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

But get a "disk read error" when doing so. I understand that if I had my Windows disk plugged in at the time of install that GRUB would have automatically put it into the load options file...but, alas, I did not. Is there anyway to either 1. add this in manually without the errors or 2. re-install grub so that it will find this automatically?

---

### Post by bernied on 2006-09-04
The problem with your entry for windows is that windows only likes to be on the first disk. But this doesn't mean that you have to change the disk order. Try adding these two lines, after the 'root' line in the windows entry:

map (hd0) (hd1)
map (hd1) (hd0)

These two lines tell grub to change the order of the two disks so that windows thinks it is on the first one (at least that's my understanding).

You can leave off the 'makeactive' line completely - this sets the boot flag on the specified partition (does not affect disk order) - or you can leave it in, it will make no difference unless you messed with the windows disk (if you removed that boot flag using fdisk or similar).

Please let me know if this worked.

---

### Post by frequenicity on 2006-09-04
Added that and I am still getting a "disk read error"

Before this I have just been physically changing the IDE cable from one drive to another which was working fine...but I would rather be able to dual boot without doing that...since that's not really dual booting at all.

Is there a command I could use to make sure that the drive I am going for really IS (hd1,0)? It makes sense that it is, but I also have another NTFS drive that is a storage drive which is connected through IDE2

---

### Post by bernied on 2006-09-04
You can work this out using the grub console.
When you boot up, at the grub boot menu, hit the 'c' key. This will give you a command line. You can use tab-completion and the cat command to find what files are in the base directory of your partitions. So, in the grub console try some of this (when I write <TAB> I mean hit the tab key and anything with a # in front is a comment, don't type it):
```
root (<TAB>
# you should get a list, choose one
root (hd0,<TAB>  # for example, try the others as well 
# this time you should get a list of partitions
root (hd0,0)     # again, for example
cat /<TAB>       # now you should get a list of files
# then try again with a different disk/partition
root (hd1,0)
cat /<TAB>       # etc
```
You can do this for each directory, or even for each partition. The list of files should give you enough indication. If in doubt place a unique file in the root directory of the first partition of each disk before you try this.

---

### Post by hoodwink on 2006-09-04
> **frequenicity said:**
> A little background:
I have installed Ubuntu on a clean HD that is dedicated to linux and seperate from my Windows drive. I have this on the primary channel of IDE1. My Windows drive is on the slave channel of IDE1. manually without the errors or 2. re-install grub so that it will find this automatically?
Lets split this into two problems:

1. Did grub get written to your primary drive - ie can you boot Ubuntu?

a. Yes. Then boot Ubuntu and 'sudo su -' (enter your password), then edit '/boot/grub/menu.lst'

b. No. You need a LiveCD (Ubuntu or Knoppix will do). 
(1) Boot from the LiveCD
(2) Become root (on Knoppix this is 'su -' (no password required). I don't know about the Ubuntu LiveCD. Someone else can chime in with instructions.
(3) Enter 'mount /dev/hda /mnt' (or some other mountpoint)
(4) Edit '/mnt/boot/grub/menu.lst'.

2. Fixing the menu.lst

a. Your Ubuntu boot stanzaappearsto be correct.

b. Try adding the  following stanza for booting Windows. Most versions of Windows don't like to be booted from other than the first partition on the primary drive, so this will cause grub to pretend that your Windows drive is the primary.

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

c. Save the menu.lst

d. If running frun the LiveCD (ie Ubuntu was not bootable), enter grub and at the grub prompt, enter
   root (hd0,1)
   setup (hd0)
   quit
   umount /mnt

e. If running from Ubuntu, saving the menu.lst is sufficient.

f. Remove LiveCD (if any) and reboot.

HTH,

---

### Post by frequenicity on 2006-09-04
> **hoodwink said:**
> 
b. Try adding the  following stanza for booting Windows. Most versions of Windows don't like to be booted from other than the first partition on the primary drive, so this will cause grub to pretend that your Windows drive is the primary.

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

c. Save the menu.lst



I added that stanza but still the same result. It IS indeed hd1,0 that I am aiming for, however it is an "unknown file system" though I am guessing that is standard?

---

### Post by bernied on 2006-09-04
Try replacing
root (hd1,0)
with
root (hd1)

---

### Post by bernied on 2006-09-04
And you can try out all of these options directly from grub. This will save you the time of rebooting ubuntu to change the menu.lst then shutting down ubuntu. When you get the right commands, then fix them in menu.lst.

Just reassure me that you can still boot windows when you swap those cables around - did I read that right?

---

### Post by frequenicity on 2006-09-04
Yes that is correct. I can boot both systems without problems by switching the cables. I am on my way out, so I will try these things this afternoon when I return. Thanks to everyone for all your help! Will keep you posted.

---

### Post by bernied on 2006-09-04
You might also want to try replacing 
root
 with 
rootnoverify 
(but only on that windows entry)

It's not XP Professional is it?

---

### Post by frequenicity on 2006-09-04
No, XP home.

---

### Post by bernied on 2006-09-05
So, still no joy?

---

### Post by frequenicity on 2006-09-05
Still not working. I have tried issuing "unhide" commands to the drive and everything. Just still gets held up after the "root" or "rootnoverify" command. 

Oh well. It's only another month or so before I build my new gaming PC so I will have this one just for Ubuntu. It's not the biggest deal in the world...just thought maybe someone else had experienced the problem before. It's probably the fact that they are on two seperate hard drives that makes it a bit unique..

---

### Post by bernied on 2006-09-05
Your situation is not unique. I boot windows and ubuntu from separate drives using grub. The difference in my setup is that the windows is on the primary drive and ubuntu on the second. So the mbr in the windows drive points to grub on the /boot partition on the second drive. Mine works fine. Grub can do this.

If you want to keep trying, there are a few things you could check:
Are the map commands after the root (or rootnoverify) command on that windows entry?
How are you so sure that (hd1,0) is the correct target, if grub was unable to read the partition?
Can you post the output of:
sudo fdisk -l
and
ls /boot/grub/

What happens when you do the following in the grub console:
```
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
boot
```
Unhide will only make a difference if you have otherwise hidden the partitions - you can see this from the output of fdisk -l

Also are you sure you have the correct jumper settings for the drives when your ubuntu drive is first? Can you interrupt the boot sequence before grub comes up (usually with the delete key or maybe F5) so you can see the BIOS settings. Is the second disk visible there?

---

### Post by bernied on 2006-09-05
The following is from the grub manual. You can see they mention a couple of cases when map won't work, and when booting Windows won't work because there are more than one windows partition on a disk.
> GRUB cannot boot DOS or Windows directly, so you must chain-load them
(*note Chain-loading::). However, their boot loaders have some critical
deficiencies, so it may not work to just chain-load them. To overcome
the problems, GRUB provides you with two helper functions.

   If you have installed DOS (or Windows) on a non-first hard disk, you
have to use the disk swapping technique, because that OS cannot boot
from any disks but the first one. The workaround used in GRUB is the
command `map' (*note map::), like this:

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)

   This performs a "virtual" swap between your first and second hard
drive.

   *Caution:* This is effective only if DOS (or Windows) uses BIOS to
access the swapped disks. If that OS uses a special driver for the
disks, this probably won't work.

   Another problem arises if you installed more than one set of
DOS/Windows onto one disk, because they could be confused if there are
more than one primary partitions for DOS/Windows. Certainly you should
avoid doing this, but there is a solution if you do want to do so. Use
the partition hiding/unhiding technique.

   If GRUB "hide"s a DOS (or Windows) partition (*note hide::), DOS (or
Windows) will ignore the partition. If GRUB "unhide"s a DOS (or
Windows) partition (*note unhide::), DOS (or Windows) will detect the
partition. Thus, if you have installed DOS (or Windows) on the first
and the second partition of the first hard disk, and you want to boot
the copy on the first partition, do the following:

     grub> unhide (hd0,0)
     grub> hide (hd0,1)
     grub> rootnoverify (hd0,0)
     grub> chainloader +1
     grub> makeactive
     grub> boot

---

