---
title: "XP/Kubuntu Dual Boot Issues..."
date: 2005-06-02
forum: Desktop Environments
---

### Post by ryansteyn on 2005-06-02
Hi all

Firstly, I am a nOOb at linux, but know my way around Windoze.
Secondly, I did search for this issue but found nothing....

I have 2 hdds in my machine, a SATA drive running XP Home (NTFS) and a slave PATA running Kubuntu (ext3 and swap partitions, Kubuntu's auto-choice). XP was loaded first and all was fine. Then loaded Kubuntu 5.04 and it loaded fine and picked up XP, then set up the GRUB for dual boot.

When I boot with SATA drive first in boot order, No dualboot options at all. XP loads fine.
When I boot with PATA drive first in boot order, I get the dual boot and Kubuntu loads fine but when I try to choose XP from the dual boot I get.....

"root (hd1,0)
filesystem type unknown. partition type 0x7
savedefault
makeactive
chainloader +1"

It then sits there forever. Prob a dumb question but please help!! I have no idea how to get the XP boot option to load.

---

### Post by Takis on 2005-06-02
Hi duder.
It sounds like GRUB wrote to the Master Boot Sector of your PATA drive, rather than the SATA. Not like it makes a difference which physical drive it's on, it's where it is in relation to the OSs that matters. If I remember correctly, you should install GRUB on your Windows drive (you get this option during installation time. Post-install, I'm not sure how to do it).

---

### Post by boby on 2005-06-03
I think I had the same problems, grub uses your PATA disk like first disk and the SATA disk like second disk.
Windows knows boot only the first disk.
for testing :
when you are in the grub menu during the boot,  press button c
tap this :

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
grub> root (hd1,0)                 hd1 = second disk, 0 = boot partition of windows
grub> chainloader +1
grub> makeactive
grub> boot

[http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)

If that works, you will add the both line map in the /boot/grub/menu.lst.

---

### Post by ryansteyn on 2005-06-04
[QUOTE=boby]I think I had the same problems, grub uses your PATA disk like first disk and the SATA disk like second disk.
Windows knows boot only the first disk.
for testing :
when you are in the grub menu during the boot,  press button c
tap this :

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
grub> root (hd1,0)                 hd1 = second disk, 0 = boot partition of windows
grub> chainloader +1
grub> makeactive
grub> boot

[http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS-Windows.html#DOS%2fWindows)

If that works, you will add the both line map in the /boot/grub/menu.lst.[/QUOTE]
 Thanks boby!!

That cleared it up by entering it maunually, just need to work out how to edit the menu.lst file as when it installed Kubuntu it wont let me login as root and the file is locked :(

---

### Post by themelvin on 2005-06-04
ryansteyn, try this:
sudo nano /boot/grub/menu.lst
enter your password

edit in nano and save, it should be OK now.

---

