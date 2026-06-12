---
title: "Annoying, annoying problem with 8.04 and Inspiron :("
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BoyanSemerdzhiev on 2008-05-21
So I just got the 8.04 LTS CDs in my mailbox and like a kid with a new toy, I was eager to try it out. I own a humble Inspiron laptop with the following specs: AMD Turion X2 64bit@1600 MHz, 2GB@667MHz Kingston RAM, 120 GB SATA Samsung HDD and an ATI onboard GPU. BIOS version: 2.6.3.

It boots the Live CD just fine and quick, I go through the collection of personal info, set up a ext3 and a swap partition just right, and then it starts. 
First it hangs just before the start of the installation, on "Creating Ext3 File System" for about 5 minutes before resuming. Then everything is fine until i try to boot the fresh-installed OS. The booting process takes between 7 and 8 minutes. I removed the "quiet" and "splash" parameters from the kernel boot line and it seems to stall on three different messages in a loop:

1) ata1: SATA link up 1,5 Gbps(SStatus 113 SControl 300)
2) ata1: failed to recover some devices, retrying in 5 sec
3) [sda] Write cache: enabled, read cache: enabled, does not support ...

Additional info:
1) I read reddeadresolve's articles about installing Ubuntu on Inspiron 1501. Although I couldn't find any connection between my problem and the solutions described by him, I tried them and they didn't work.

2) I tried adding both "pci=nomsi" and "hda=noprobe" parameters to the kernel boot line, neither worked. (read about it in a slackware forum).

Any help on the problem would be appreciated.

---

### Post by irish8890 on 2008-05-21
To fix this you might want to try the additional boot parameters (<F4> or <F6>, not sure which one) and select "noapic" & "nolapic".

Hope this helps.

John

---

### Post by BoyanSemerdzhiev on 2008-05-21
> **irish8890 said:**
> To fix this you might want to try the additional boot parameters (<F4> or <F6>, not sure which one) and select "noapic" & "nolapic".

Hope this helps.

John
No good, but thanks.
Any other suggestions?

---

### Post by BoyanSemerdzhiev on 2008-05-23
Come on dudes, I'm desperate :roll:

---

### Post by bthoward on 2008-05-23
Try the previous two options and add acpi=off to that.

---

### Post by BoyanSemerdzhiev on 2008-05-30
No good. More suggestions please.

---

### Post by Darth Lukan on 2008-05-30
I also run Hardy on a Dell Inspiron 1501 Laptop.  If it helps, my installation of Ubuntu recognizes my hard drive as /dev/sda and my external drive as /dev/hda with cdrom0 being /dev/hdb.

I should have the same kind of HDD as you, SATA connection and all.  Maybe if you change your mount point names.  Here is what my GRUB loader uses (check /boot/grub/menu.lst:

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5ccb639c-1f21-47de-bfd9-f4c7495439c8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

My biggest problem with the install was the support of my ATI Radeon Xpress 1150, but that's another topic.  Hopefully that info above helps.  AT the worst you might have to re-install and take extra care to take note of how the system sees your hard drive (sda, hda, hdb...).

---

### Post by Laeth on 2008-05-31
Have you tried using the Guided partition option during install?
I have a Inspiron 1721 with similar Specs (close enough at least) and Guided, while not always ideal, did work for me.

Also, do you have the 64bit version of the release? I find more errors occur if you just use the regular disks.

---

