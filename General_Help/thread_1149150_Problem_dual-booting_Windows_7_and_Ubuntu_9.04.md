---
title: "Problem dual-booting Windows 7 and Ubuntu 9.04"
date: 2009-05-04
forum: General Help
---

### Post by JECHO on 2009-05-04
Hey guys I am having a problem dual booting windows 7 with ubuntu 9.04. Here is my setup:

Two 500GB internal drives. I have installed windows 7 on sda and Ubuntu 9.04 on sdb Normally I dualboot XP or Vista with ubuntu on this machine using that same partition scheme but one i tried setting it up with windows 7 and ubuntu 9.04 i ran into this problem... 

When i turn on the machine i normally see GRUB but with this configuration I do not. It boots straight into windows as if there is no boot loader installed at all. I haven't been able to figure out why it does this but i have noticed that windows 7 creates a small "system" partition that older versions of windows did not. maybe this is interfering with GRUB in some way? I don't know.

Anyway, the way I have been getting around this problem is by entering the the one-time boot menu and manually selecting my second drive(the one with Ubuntu 9.04 on it). This technique sends me straight to GRUB and I can select the Ubuntu option. (no, there are no options for any windows OS).

Basically what i am asking is if any of you know what I need to add to the menu.list file in order for it to see windows 7? Or if i need to do something entirely different? :confused:

Please help, I would really love to get this fixed!

Thanks in advance for any and all help.

---

### Post by caljohnsmith on 2009-05-05
To save you from having to manually select the Ubuntu drive to boot first on start up, can you go into your BIOS settings and there specify the Ubuntu drive to be first in the boot order? But to answer your question about booting Windows 7 from Grub, you should be able to do that, so how about first pulling up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the bottom of the menu.lst file:
```
title Windows 7
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Let me know how that goes or if you run into problems.

John

---

### Post by JECHO on 2009-05-05
> **caljohnsmith said:**
> To save you from having to manually select the Ubuntu drive to boot first on start up, can you go into your BIOS settings and there specify the Ubuntu drive to be first in the boot order? But to answer your question about booting Windows 7 from Grub, you should be able to do that, so how about first pulling up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the bottom of the menu.lst file:
```
title Windows 7
rootnoverify (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Let me know how that goes or if you run into problems.

John

Thanks a lot man, that worked! :guitar:

---

### Post by caljohnsmith on 2009-05-05
> **JECHO said:**
> Thanks a lot man, that worked! :guitar:
Glad to hear that worked OK; cheers and enjoy your dual-boot setup. :)

John

---

### Post by dstarfire on 2009-05-05
Alternatively, you could simply add linux to your windows 7 boot menu. Just download a (free) copy of easybcd which has a built-in option to add a boot entry for linux. 

Only drawback I've found is that on my system it pops up some stupid error message every boot, but will continue to boot grub normally once you type [Spacebar].

---

### Post by devosion on 2009-05-20
Im currently in the process of getting my dual-boot setup to work, but no matter how many times I reinstall grub and ensure my menu.lst settings are correct it will not boot into grub. I have attempted to change my drive boot order, since I have two drives sda (my windows 7 drive and partition) and sdb (my ubuntu drive and partition). When I run fdisk -l it shows both drives having a boot partition. Im getting to the poin where I will reinstall ubuntu just to see if it will fix the problem, as it worked on my laptop for dual-boot, but before that I need suggestions for deleting the Windows 7 bootloader. I have tried to edit the Windows 7 boot settings in msconfig, but since it is the only boot configuration it see's it won't let me delete it. Any help would be appreciated.

---

### Post by Ampi on 2009-06-07
Hmm, I am having the exact same problem. Only difference is that I have both OS's on one harddisk, windows 7 on the primary partition and ubuntu on the extended partition. 

I changed the boot menu but now my computer boots automatically into Ubuntu without the option for Windows 7, though I added it to the menu.lst. 

Any idea how I can get Windows 7 back without losing Ubuntu?

---

### Post by Ampi on 2009-08-21
Sorry for the bump, but does nobody have an idea?

---

