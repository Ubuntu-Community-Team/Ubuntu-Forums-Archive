---
title: "Error 22 in GRUB after new installation"
date: 2008-12-04
forum: General Help
---

### Post by ghizzle20 on 2008-12-04
Hello everyone,

This may not be an Ubuntu problem, but im more farmilar with that so i decided to post here:

I am an ubuntu user, but recentley a friend told me about openSUSE, so i created a hard drive partition to try it out. The install went smoothly, but when i rebooted, it said GRUB Error 22. I can't boot into anything to fix anything, so im kinda stuck. Any ideas? 

Thanks

---

### Post by caljohnsmith on 2008-12-04
You could reinstall Grub to the MBR (Master Boot Record) so that it uses the menu.lst in your Ubuntu partition rather than the OpenSUSE partition; then you can add an entry in your Ubuntu menu.lst to boot OpenSUSE. If that sounds good to you, then how about booting one of your Live CDs, open a terminal (Applications > Accessories > Terminal in Ubuntu), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu and OpenSUSE partitions (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4). Choose the one that is Ubuntu, knowing that:
```
sda1 = (hd0,0)
sda2 = (hd0,1)
sda3 = (hd0,2)
...etc.
```
And then use it as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Then when you reboot, you should get the Ubuntu Grub menu again. To add OpenSUSE to your Ubuntu's menu.lst, first boot into Ubuntu, open a terminal and do:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom:
```
title OpenSUSE Grub Menu
configfile (hdX,Y)/boot/grub/menu.lst
```
And change (hdX,Y) to the OpenSUSE partition. Then you should be all set, but let me know if you run into problems.

---

### Post by ghizzle20 on 2008-12-04
alright that sounds good.  thannks alot. ill try it and see how it goes

---

