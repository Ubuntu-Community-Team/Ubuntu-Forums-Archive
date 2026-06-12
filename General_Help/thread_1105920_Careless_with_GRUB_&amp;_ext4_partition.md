---
title: "Careless with GRUB &amp; ext4 partition"
date: 2009-03-25
forum: General Help
---

### Post by AndyCee on 2009-03-25
I installed Jaunty on an ext4 partition (sda5) to try it out, using my Intrepid partition (sda1) for normal use and sharing my home partition (sda3).

I wanted to boot from my Intrepid partition, and carelessly did the following:

$ grub-install /dev/sda

I thought this would update the menu.lst file in sda1, but no.

SO. I can access my Intrepid partition fine, but the grub menu points to outdated information on sda5, and won't boot to Jaunty installed there. My Intrepid kernel (2.6.27-11) doesn't support ext4, so I can't just mount it and copy the menu.lst file over. I could try and manually insert a grub boot option, but I can't remember what kernel version I have installed there.

What is the easiest way to regain access to the partition?

---

### Post by dzv on 2009-04-03
Did you grub-install from Jaunty or Intrepid?  My understanding is that you need to grub-install from Jaunty (or manually upgrade your GRUB in Intrepid) in order to install a version of GRUB that supports ext4.  I believe that if you have the Intrepid version of GRUB installed, then even if you had it configured correctly, I'm not sure it would be able to boot the ext4 partition.  I'm not 100% sure about this, though.

But, assuming you did grub-install the newer version of GRUB (or that what I've said above is wrong), you can probably boot into Jaunty by dropping to the GRUB shell at bootup and launching manually.  Press 'esc' as soon as you see GRUB starting, and then press 'c' to enter command line.  From there, you need to figure out how where to tell GRUB to boot from.  If you have only one physical disk, then the HDD should be hd0.  So, in the GRUB shell, you can try something like this (typing 'enter' after each line)

```
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic
initrd /boot/initrd.img-2.6.27-11-generic
boot
```

Note that (hd0,4) would be the 5th partition on the 1st HDD, as the counting starts from 0.  Once you've specified the root, all other paths are relative to that (eg. /boot/ refers to the /boot/ folder on hd0,4).

Replace the vmlinuz**** and initrd.img-***** with the correct filenames for your Jaunty installation.  You can also use tab-autocomplete in GRUB to make this easier.  So, you can start typing "kernel /boot/" and then press the 'tab' key to see what suggestions are available.  This will also be an easy test to see if GRUB is able to read the ext4 partition or not.

---

### Post by AndyCee on 2009-04-17
Yeah, thanks. No, it didn't work.

Grub didn't seem to want to know about the other partition, and I've gone to the length of reinstalling Jaunty on /dev/sda5.

Thanks for the idea though.

---

