---
title: "dual booting with windows XP"
date: 2008-03-27
forum: Desktop Environments
---

### Post by ddeus2003 on 2008-03-27
hi all
Its the first time i ve installed the Ubuntu operating system and the first time that I use this forum! I have two disks installed on my pc! The first one whos size is 320gb is divided into two partitions on  the first of which i ve installed WIndows! I wanted to get a glimpse of Ubuntu so i made two partitions on my smaller 120gb disk. The first partition is to be used for swap (about 3Gb) and the second one which is about 40gb would be used for Ubuntu's installation! The problem is that after the installation although i expected for ubuntu's bootloader to "see" windows as an existing operating sys it didnt so the only option i have for booting is Ubuntu! Can you plz help! I will upload two printscreens so you can see how my disks are divided

Windows is installed under /media/sd1

I would appreciate if you replies would be as simple as possible!
I ve tryed tweaking grub myself but there are many details that i ignore!

---

### Post by Jimmy Johnson on 2008-03-27
You need to add this to your /boot/grub/menu.lst

title Microsoft Windows XP at sda1
rootnoverify (hd0,0)
chainloader +1

---

### Post by ddeus2003 on 2008-03-27
I get invalid or unsupported executable format!

---

### Post by Islington on 2008-03-27
> **ddeus2003 said:**
> I get invalid or unsupported executable format!

you need to add it in ubuntu

so boot up ubuntu 
open a terminal from applications>accessories
type in ```
 sudo gedit /boot/grub/menu.lst 
```

now it will ask for you password, type it in.

now a basic text editor will pop up

add these three lines to the end.
```

title Microsoft Windows XP at sda1
rootnoverify (hd0,0)
chainloader +1

```

save and exit.

reboot your computer.

---

### Post by LinuxLovingFalla on 2008-03-28
dont do it man :) 

linux is much better

all i can say is my expreience has been bad with it cuz it removed 2 partns i had before. you know it ruined my work :|

---

### Post by ddeus2003 on 2008-03-28
I ve followed your instructions but i still get invalid or unsupported executable format!!
I think by using hd0 i dont point the bootmanager in the right direction since i have two disks and windows is on the first and linux on the second one ! 
Can you also explain what is the second number after hd0 standing for ?? In our example the 0 (hd0,0)<-

---

### Post by Jimmy Johnson on 2008-03-28
(hd0,0) is grub talk for the first drive, first partition.

Ok, give this a try, open a console and type: sudo update-grub

That will update your /boot/grub/menu.lst, see if that will add your Windows to the menu.

If that don't work then post a copy of your "menu.lst" and "/etc/fstab" and we will be able to see how things are configured.

---

### Post by rico4295 on 2008-03-28
I installed Ubuntu on a second hd. That drive is ide and my xp drive is sata, which i used to boot to. Now I boot to the second drive in bios because that is where the grub boot loader is. The option are there and each os boots fine.

---

