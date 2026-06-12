---
title: "Installing and adding Windows XP to the Grub boot menu as a secondary OS?"
date: 2008-12-28
forum: General Help
---

### Post by Pipps on 2008-12-28
I am hoping you can help me...

I use Ubuntu all day, every day, and I am very pleased with it. However, the requirement has arisen for me to run one or two specific Windows-only programs for multimedia processing. Yes, begrudgingly, I may have to experience an XP boot once in a while, again.

So I would like to run Windows XP as a secondary operating system. Hopefully, as a second option from the Grub boot-loader at my system's startup?

I only have 1Gb of RAM and so a Virtual Machine or Virtual PC approach would not appear to be feasible for my hardware. I should therefore prefer to take a dual-boot approach, as the infrequent multimedia processes which I would occasionally perform under Windows would also be rather memory-intensive.

I have an MSI Wind, a fully legal copy of Windows XP in ISO image file format, and a formatted USB pendrive. So I am hoping that I might be able to make the requisite installation. I will definitely need your help if I am to get there!

My hard drive is currently partitioned as follows:

sda1 - /boot (ext3)
sda6 - / (ext3)
sda7 - swap (n/a)
sda8 - /usr (ext3)
sda9 - /var (ext3)
sda10 - /home (ext3)

So without further ado, and in case it helps, here are the points on which I hope you can advise me:

1. Would I begin by using GParted to create an extra two partitions - one for the XP installation, in FAT32 format, and another empty FAT32 space to be shared by both OSs? If so, how should I go about doing this?

2. Once I have my partitions in a row, how should I go about installing XP on its newly allocated FAT32 partition? Would I simply boot from startup with my USB pendrive plugged in, and my bootable XP iso ready, and simply install XP on the relevant newly created partition?

3. How should I then tell the Grub boot menu to give me the additional option of booting from another operating system which is now installed on a different drive?

4. Would I then be ready to go?

One thing which I definitely won't be allowing, is for the XP operating system to ever have access to the internet. I'll be unplugging my ethernet whenever I boot it!

I look forward to your replies. Thank you for your help!

---

### Post by SlidingHorn on 2008-12-28
Here's a good step-by-step for this:  [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by caljohnsmith on 2008-12-28
> **Pipps said:**
> 
My hard drive is currently partitioned as follows:

sda1 - /boot (ext3)
sda6 - / (ext3)
sda7 - swap (n/a)
sda8 - /usr (ext3)
sda9 - /var (ext3)
sda10 - /home (ext3)

So without further ado, and in case it helps, here are the points on which I hope you can advise me:

1. Would I begin by using GParted to create an extra two partitions - one for the XP installation, in FAT32 format, and another empty FAT32 space to be shared by both OSs? If so, how should I go about doing this?

That sounds good, but be sure to create a primary partition (preferably NTFS) for Windows, not a logical partition. Also, when you resize your ext3 partition(s), their UUIDs will change; I would recommend doing:
```
sudo blkid
```
Before doing your resizing, and once you are done, check the new UUIDs with the same command, and if they are different, you can restore the original UUIDs using:
```
sudo tune2fs -U "[COLOR="Blue"]<original UUID>[/COLOR]" /dev/[COLOR="Blue"]sdXY[/COLOR]
```
So you would copy/paste the original UUID into the command above, and also change sdXY to the partition you want to change. 
> **Pipps said:**
> 
2. Once I have my partitions in a row, how should I go about installing XP on its newly allocated FAT32 partition? Would I simply boot from startup with my USB pendrive plugged in, and my bootable XP iso ready, and simply install XP on the relevant newly created partition?

I don't think I follow you--are you going to try and install the Windows ISO to your pen drive and boot that? Or what is on your pen drive? 

Also, once you install Windows, it will overwrite Grub in the MBR, so to restore Grub you can do the following from the Live CD:

```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
> **Pipps said:**
> 
3. How should I then tell the Grub boot menu to give me the additional option of booting from another operating system which is now installed on a different drive?

4. Would I then be ready to go?

I can help you modify your Grub menu.lst to include XP once you have it installed if you want. Just post the output of:
```
sudo fdisk -l
```
Once you have XP installed. We can work from there if you want.

---

### Post by Pipps on 2008-12-29
> **SlidingHorn said:**
> Here's a good step-by-step for this:  [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
Thank you. I will definitely give that article a good read this evening.

---

### Post by Pipps on 2008-12-29
Hi caljohnsmith

Thank you so much for your incredibly detailed and helpful comments and code. I will try my very best to get my head around it and to implement it as you have prescribed.

Yes, I was thinking of making a bootable XP pendrive with the XP ISO, and installing XP onto its newly allocated partition that way. Would that be a good approach?

I note that Windows will interfere with Grub. Thank you for the command on how to reinstate it.

My understanding of your advice is that once Grub has been reinstated, my system will only boot Ubuntu from startup, until we further modify Grub afterwards to include XP in the list?

So I'll still be able to login to Ubuntu after the XP installation and the Grub reinstating, providing I keep a printed copy of your prescription close to hand? Is that correct?

Also, thank you for pointing out that I should make the XP partition NTFS and Primary, not Logical. That sounds like a potential life-saver, there.

One further question on this point - if I one day wanted to get rid of the XP installation and move back to a more streamlined system or save on disk space, could I then potentially merge the NTFS partition back into my Ubuntu ext3 /home drive? Is this sort of partitioning trickery possible? It's not a definite plan, but just a thought, at this stage.

Thank you again for all your help. I'll keep you posted on my progress.

---

### Post by caljohnsmith on 2008-12-29
> **Pipps said:**
> 
My understanding of your advice is that once Grub has been reinstated, my system will only boot Ubuntu from startup, until we further modify Grub afterwards to include XP in the list?

So I'll still be able to login to Ubuntu after the XP installation and the Grub reinstating, providing I keep a printed copy of your prescription close to hand? Is that correct?

Yes, that's exactly right, if all goes well you should be able to boot into Ubuntu after reinstalling Grub, and then it is a simple matter of adding XP to your Grub menu; I'll be happy to help with that if you would like any assistance. :)
> **Pipps said:**
> 
Also, thank you for pointing out that I should make the XP partition NTFS and Primary, not Logical. That sounds like a potential life-saver, there.

One further question on this point - if I one day wanted to get rid of the XP installation and move back to a more streamlined system or save on disk space, could I then potentially merge the NTFS partition back into my Ubuntu ext3 /home drive? Is this sort of partitioning trickery possible? It's not a definite plan, but just a thought, at this stage.

Thank you again for all your help. I'll keep you posted on my progress.
Yes, merging the XP partition with your /home partition is possible, but only if the two partitions are physically next to each other. From what you posted in your first post, that might not be your case though, but that depends entirely on which partition(s) you shrink to make the XP partition. If you would like further help with that, please post:
```
sudo fdisk -lu
```
So I can see the physical layout of your partitions. Anyway, good luck and let me know how it goes. :)

---

### Post by Pipps on 2009-01-03
Hello again! 

I have run into a small issue and I hope you might be able to guide me through it.

I rebooted Ubuntu in LiveUSB mode, ran the Partition Editor, and reduced the size of my /home partition in order to allow for two new partitions to be created. I clicked 'Apply'... and waited.

All tasks completed successfully, and after the filesystem refresh, I could see a nice unallocated space for my new partitions to be created in.

I remembered the wise words of advice that I received earlier in this thread:

[QUOTE=caljohnsmith]...be sure to create a primary partition (preferably NTFS) for Windows, not a logical partition.[/QUOTE]

But when I proceeded selected the new unallocated space and attempted to create a new partition within it, I only had the option to create a logical partition. In the drop-down menu, the 'Primary' option was grayed out and unselectable. I tinkered around in the Partition Editor for a little while longer, but could find no way of creating a primary partition in this new space.

I considered the possibility of selecting the option of creating a whole new file system, and perhaps leaving the previous partitions intact and maybe finding an option to creating a new primary partition that way, but the grand warning message the all of 'sda' would be overwritten, made me think twice before attempting it. At this stage, I thought it would be best to revert to the experts' guidance.

How may I create a new primary partition in the now unallocated space at the end of my hard drive?

---

### Post by caljohnsmith on 2009-01-03
Please post the output of:
```
sudo fdisk -lu
```
And identify your partitions. I suspect your /home partition is a logical partition, so the space that you freed up will be part of the extended partition; if that's true, that is why gparted will only let you create a logical partition.

---

### Post by Pipps on 2009-01-03
You're absolutely right - my /home partition is a logical partition.

Is it generally preferable for a /home partition to be primary or logical as a rule of thumb?

---

