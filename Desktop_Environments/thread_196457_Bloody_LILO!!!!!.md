---
title: "Bloody LILO!!!!!"
date: 2006-06-14
forum: Desktop Environments
---

### Post by kickstar on 2006-06-14
hello all,

right this is the bottom line, before last night i had the setup below...

_**First HDD (hda) - 80Gb**_
hda1=WindowsXP - NTFS
hda2=Dapper Drake - ext3
hda3=Linux Swap

_**Second HDD (hdb) - 8Gb (very old)**_
hdb1=FAT32

im looking for a lightweight distro to run on my old laptop so i downloaded the ISO for Vector Linux, burnt it and just when i was ready to get the lappy out i had a stupid idea *I know, why dont i install it to the second hard drive here on my desktop... that way i can try it without moving from my chair *

well it all seemed quite logical last night... i wouldn lose any files because *hdb* was empty. i installed vector linux quite easily - the installer is alot like slackware's - one thing that i knew i had done wrong was say yes to "do you want to install LILO to the MBR?" at the time i thought that this wouldnt effect grub because it was on a different disk....

well it did and now i can only boot windows or Vector Linux... i can boot 6.06 by booting from the VL install disk and giving it the perameters. but this only allows me to use the command line coz for some reason my xorg.conf got screwed while i was installing VL (dont ask me how!)

im guessing i overwrite the grub boot loader with lilo, how can i undo this please cos if i cant then im gonna have to reinstall Windows (cos my girlfriend needs iTunes) - theres another thing if someone could suggest a program that can deal with her ipod i could get rid of windows altogether Yipeeeeee! (tried gtkpod to no avail) its a nano if that makes any difference?

anyway yes i need to know if i can reinstall grub to the MBR without losing any files... if need be i suppose i could reinstall dapper.

thankyou to everyone that helps me!

screw anyone that doesnt!

thanx.

---

### Post by Ramses de Norre on 2006-06-14
You can boot into dapper with the vector linux live disc? Do that and from terminal run ```
sudo grub-install hdXX
```  and replace hdXX by the device node of the drive you boot from.

---

