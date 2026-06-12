---
title: "Ubunto installed and BOOTMGR and GRUB lost at reboot."
date: 2008-07-17
forum: Desktop Environments
---

### Post by Raphial on 2008-07-17
Hi, Raphial here.

I installed Ubuntu 7.10, since I did not have the latest CD of 8.04, and I installed it on my Toshiba Satellite laptop with Windows Vista from booting from the CD and those methods and successfully installed it.

I've used Ubuntu for a day or two now, and the last time I used Vista, and shut down the computer and turned it back on, a "Grub missing ERROR21" message appeared. I researched this and found out the GRUB file is in the wrong system folder and not in the boot folder, or it's been deleted somehow.

So I burned Super Grub on a CD and booted from it (Google it lol) to fix the problem, but come to find out my BOOTMGR of Vista's boot file is gone too. I don't have a Vista CD to just reinstall BOOTMGR like new, so I don't know how to fix that problem, nor the GRUB ERROR21 problem because GRUB isn't detected ANYWHERE on the laptop's hard drive, which is really weird because I haven't tempered with any system files or anything since I'm new to Ubuntu.

Any suggestions? I obviously cannot this laptop at all at the moment, and I really don't plan on loosing this new laptop.

---

### Post by NoJock on 2008-07-17
Here is a file location you can down load and burn a bootable windows vista recovery disk it works.
neosmart.net/blog/2008/windows-vista-recovery-disc-download
Fix the windows (Vista) and the you can fix Ubuntu.

---

### Post by Raphial on 2008-07-17
> **NoJock said:**
> Here is a file location you can down load and burn a bootable windows vista recovery disk it works.
neosmart.net/blog/2008/windows-vista-recovery-disc-download
Fix the windows (Vista) and the you can fix Ubuntu.

Alright. Cool. Got it to work. Alright, now to fix the Grub issue. When I go to install the GRUB using Super Grub, the BIOS gets an error. Error15 File not found.

"findf /grub/stage1 /boot/grub/stage1

Error15: File not found"

Is there a way to repair this from the BIOS? I'm fairly new at Ubuntu, or Linux in general; any suggestions?

---

### Post by logos34 on 2008-07-17
Since you've only been using ubuntu a few days I would recommend reinstalling (8.04 this time).  Hopefully the problem will not be repeated

---

### Post by dreadmeat on 2008-07-17
[http://www.vistabootpro.org/](http://www.vistabootpro.org/) fixed some problems i had a while ago.


edit: this is a bit 'smaller' [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

