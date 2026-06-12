---
title: "GRUB BIOS bootup issues"
date: 2007-07-08
forum: Dell  Ubuntu Support
---

### Post by BriGaid on 2007-07-08
Hello everyone and thanks for taking to time to read this.

I currently have a dell dimension 3000 computer which was previously dual-booting windows and ubuntu 7.04.  This morning I decided to reformat my hard drives and get rid of Windows once and for all.  my previous install of feisty fawn was on a secondary hard drive.  When i booted my pc up (with the windows HDD and the feisty HDD set to boot, it would give me the bios splash then GRUB.  I would choose the latest kernel and be on my way.  Now I reformated the entire first windows HDD, and installed feisty on it with a seperate /home partition.  This is where my problem is.  During installation it asked me to install GRUB and I did.  Now when I restart the computer, it shows the bios splash then just goes to a blank screen with the cursor blinking and stays there.  I figured out this was because the bios is looking for the C: partition before it gave me GRUB. :mad:  Now, I have to hit F12 at the bios splash screen to choose the master HDD to boot. out of a list of master HDD, Slave HDD, C:, CD-ROM, or USB; then it will load linux normally.  I went into my bios setup to try and change the boot sequence but the only options i was given were hard disk C: and cd-rom.  Thanks for reading and I will try to give and more information I can so you can help me solve this problem.

---

### Post by splintercellguy on 2007-07-08
Have you tried using the Super Grub CD to rectify the boot issue?

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by BriGaid on 2007-07-08
I tried using the super grub cd with a bunch of the options like boot the master record.  Will the super grub cd allow me to fix the problem so my bootup sequence is back to how it used to be or do I have to keep loading the super grub cd all of the time?

---

### Post by dimeboy99 on 2007-07-10
My question is similar but not exactly the same. I have a laptop with the internal HD loaded with Feisty and a USB HD loaded with XP. I am tired of swapping HD's for using certain applications. I would like to dual boot and keep Feisty internal since the XP HD comes with me to work some days. What do I need to edit (GRUB or otherwise) to get a the menu listing for selecting either the default Feisty or the external USB HD with XP on it? Here is a listing of my menu.lst as it is now:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5033fd43-65dc-4406-882c-0727521d441a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5033fd43-65dc-4406-882c-0727521d441a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

I have already commented out the older kernel versions. Here is a copy of my fdisk -l:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Hope that gives enough information. I really really don't want to reinstall anything if it can be avoided.

---

### Post by BriGaid on 2007-07-11
bump for help.

---

### Post by BriGaid on 2007-07-12
Bump, would reinstalling on my second hdd and not booting the first hard drive work? or would the bios still look for C?

---

### Post by BriGaid on 2007-07-13
bump

---

