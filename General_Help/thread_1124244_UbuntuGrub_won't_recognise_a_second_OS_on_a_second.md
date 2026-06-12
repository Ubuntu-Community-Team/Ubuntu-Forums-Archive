---
title: "Ubuntu/Grub won't recognise a second OS on a second drive"
date: 2009-04-13
forum: General Help
---

### Post by glubbdrubb on 2009-04-13
This question relates to [http://ubuntuforums.org/showthread.php?t=541973&highlight=duel+booting+harddrives](http://ubuntuforums.org/showthread.php?t=541973&highlight=duel+booting+harddrives)
But I don't know what is going on there so I re-ask it in my way.

I have two harddrives setup. First Ubuntu was installed on the first HDD and then Vista on the second. Now, if I want to choose which OS I want to boot, I have to change the boot order in the BIOS. This is obviosly quite awkward. 

It worked fine when both OS'es were on the same drive but as you can see from the title, I am stuck.

Is there a way to get GRUB to rescan the HDD's or something like that so it "sees" Vistsa?

Thanks


P.S. Although I have been using Ubuntu for a few years, I have not really gotten into kernel or anything like that.

---

### Post by Aubergines on 2009-04-13
The thing about grub is that it uses an entirely different method to refer to disks. The first disk on a linux system will typically be called /dev/hda (or /dev/sda if you have a sata disk) and the first partition will be 1, like /dev/hda1.
With grub it's different, it doesn't use letters and everything starts with 0 rather than 1 so (hd0,0) refers to the first disk and first partition. (hd0,5) refers to the first disk, 6th partition (or /dev/hda6). Now if your windows install is a fresh install on it's own drive and is the second disk in the system it's grub reference should be (hd1,0)

---

