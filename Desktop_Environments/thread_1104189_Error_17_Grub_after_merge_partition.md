---
title: "Error 17 Grub after merge partition"
date: 2009-03-23
forum: Desktop Environments
---

### Post by superthin on 2009-03-23
Hello everybody,

I am a newbie. I was very happy when having an Ubuntu **Hardy**. Wow, was I rather happy soon? (I don't know. Sorry for my Vietnamese - English) :(

Old struture of my HDD (an IDE 80GB Seagate ATA - not SATA):

[IMG]http://img522.imageshack.us/img522/9831/myubuntuyx3.gif[/IMG]
(Viewed from Disk management of Windows XP)

After using GParted in Hardy, my structure of HDD now:

[IMG]http://img14.imageshack.us/img14/7746/partition.png[/IMG]
(Viewed from Ubuntu Live CD 6.04 LTL)

I used Grub, Ubuntu installed after Windows XP, and Grub load into MBR and managed XP.

I cannot boot my PC now. I cannot boot from Ubuntu Live CD 8.04 LTS. Many times was fail (error IO and Squash...), a few times could boot successful). In the past, I booted with Live CD successful all time. My HDD is in good health. I checked bad sectors with some tools, no bad sector found.

I attemped to (re)install GRUB with Live CD 8.04 (when it could boot). But **error 17** (Stage 1.5) or **error 22** is being still my nightmare now.

Some information (get from live session when booting from Live CD 6.04)

[QUOTE="/boot/grub/device.map"]
(hd0)   /dev/hda
[/QUOTE]

[QUOTE="/boot/grub/menu.lst"]
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=b4aab366-a089-4b2d-9b01-b2c1991471db ro quiet splash vga=0x305
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=b4aab366-a089-4b2d-9b01-b2c1991471db ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
[/QUOTE]

2 paragraphs (in quotes) above I got after attemping grub-install from Live Session when booting with Live CD 6.04 (I've lost my Live CD 8.04) and rebooting but have no success.

Who helps me?

Thanks in advance.

---

### Post by Bakon Jarser on 2009-03-23
Try this.

[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by Sojurner on 2009-03-23
Error 17 is the error u get when it cant find GRUB. Now u may already know that but cant fix it. i had the error 17 for a while and it was making me mad. 

The way i fixed it was to load my bios and go into the boot section and change the boot order of my drives. Once i did that it loaded up with no problems. Granted i had to change them around several times becuase i had 4 drives it could have been on but it worked on the 3rd try and its been working like a champ ever since.

---

### Post by leonardo_neo on 2009-03-23
Alternatively you may also like to try the "super grub disk". Please follow the link

> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

:)

---

### Post by superthin on 2009-03-25
> **leonardo_neo said:**
> Alternatively you may also like to try the "super grub disk". Please follow the link
:)

I used an Windows XP rescure disk and fix MBR => my computer could boot with Windows XP and Grub's MBR wiped out.

I installed Super Grub Disk into my Windows XP SP2 (use Windows's version of Super Grub Disk) and restarted. The result: Super Grub Disk was overwritten my MBR. How ever, it cannot detect Ubuntu, I could boot into Windows XP only.

What should I do next?

---

### Post by Sojurner on 2009-03-25
If im thinking correct (it is early) you should be able to r un the ubuntu live CD and run the grub boot loader (or install it) from the live cd. then u should be able to edit it as well to show what you want listed.

---

