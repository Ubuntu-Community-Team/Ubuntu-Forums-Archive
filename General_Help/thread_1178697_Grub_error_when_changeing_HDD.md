---
title: "Grub error when changeing HDD"
date: 2009-06-04
forum: General Help
---

### Post by Kenin on 2009-06-04
Hi

here is an introducion of my problem xD

i have 6 physics HDD, 3 IDE and 3 sATA, but i can only plug 5 of them, so, in one HDD have installed ubuntu 9.04 and in other HDD windows xp/windows 7... the rest of de disks have normal data...

so as i can plug 5 of 6 HDD, i decided to change the SO changeing the physical HDD, beeing something like this

1 - IDE - primary master - data (boot.ini, grub)
2 - IDE - primary slave - data
3 - IDE - secondary master - data
4 - sATA - ubuntu 9.04 HDD or windows HDD
5 - sATA - data

when i start whit the ubuntu HDD, it shows the grub whith the options "ubuntu", "ubuntu (recovery mode)" and "windows vista (loader)"... and it start ubuntu without prolbems.
but when i plug the windows HDD (repleacing the ubuntu HDD) it shows me "grub stage 1.5: error 17"

note: i cannot change the position of the disks.

my question is... can i make the computer starts whit any hdd? i don't care if it starts whit the grub or the windows loader, but it can't have both OS at the same time.

thanks

---

### Post by munky99999 on 2009-06-04
In the grub menu the list basically points the loader to a specific hardware location. HD0,0 sort of idea. When you switch around hardrives; your bios changes the boot list for the hardrives. which changes the #s.

So assuming you arent having controller conflicts which makes your bios totally not notice the hardrives there.

You might simply have to proactively change:
sudo gedit /boot/grub/menu.lst

Before you shutdown everytime.

Would be better if you simply get an alternative.

-USB-hardrive adapter
-hardrive enclosure
-NAS with crossover if network isnt an option.

---

### Post by munky99999 on 2009-06-04
or I guess you could also [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and Directly boot a partition of your choice.

Also assuming you always get grub loading. You could try commandline of grub.

---

### Post by uupreti on 2009-06-04
> **Kenin said:**
> 
my question is... can i make the computer starts whit any hdd? i don't care if it starts whit the grub or the windows loader, but it can't have both OS at the same time.

thanks

I think you can only boot from one hard disk at a time which is specified in BIOS settings. But you can boot from any OS at different time. For that You have to install boot loader to their own partition not in first partition of first hard drive. 

When you put windows HDD, it shows you grub loader coz grub is already intsalled at MBR and it couldn't load images specified within the grub file. If you still want to run your windows and ubuntu regardless of your hard drive , you have to install grub in ubuntu's hard drive not in MBR of windows hard drive. Then if you plug windows hard drive, it will start windows and if you plug ubuntu drive it can load ubuntu..

---

### Post by Kenin on 2009-06-06
Moveing the grub to the ubuntu HDD works, and for windows xp/7 i had to unplug every HDD and reinstall them... a little borring but that works xD

thanks for the answers

---

