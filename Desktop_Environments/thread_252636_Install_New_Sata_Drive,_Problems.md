---
title: "Install New Sata Drive, Problems"
date: 2006-09-07
forum: Desktop Environments
---

### Post by MasterHead on 2006-09-07
Hi, i'll try to explain my prob the most clearly way, lets see if someone can help me.. :)

Yesterday i bought a new sata II drive, after instaling it in my board, it an asus A8NSLI-Deluxe, with 2 sata controllers, but just one of them is Sata II compatible, and tere i already have 3 drives, this would be the fourth one, so, i installed the drive with no problems and restart the computer, until this point there were no problems. but after getting to grub i saw the usual posibilities, multiples kernels and my windows partition so i get to start the last kernel, 2.6.15.26 i think, after this it started to run normally, the blue kubuntu splash screen and loading screen, it starts the system and it  just gets stuck there for a while, after that it gets to the console and says it couldn't find a suitable system in /dev/sdc3 where my system its suposed to be.

Turn of the computer and take off the new drive, everything perfect, as i already supposed it would, turn off again and get the drive in again, restart and push "e" during grub screen to edit my options, i'll try to put them :

my drive was in grub (1,1), as it is the second drive and the boot particion( /boot) its the second one.
and my kernel image was in /dev/sdc3 as i have /boot and / in different partitions, with / in the third one.

so my first shoot was to change the drive, and i tried (0,1) (2,1) and (3,1), neither of them worked out, as they only have one partition, so partition 1 doesn't work, until here seems logical i think. 
By this point i was already pretty upset and tired as it was late in the night and i have to wake up pretty soon for work.
So my nextstep was stop and think about it a little, installing a new drive can change my devs? i mean, the system drive is the sata conector number 2( 1 in grub since it counts from 0) but for windows it was not drive 2 and for linux it was drive sdc( the third one) so it seems that it puts first of all the third drive as sda, the first one as sdb and  the second one as sdc, might it be posible that adding the fourth drive it moves te dev assignment? might it be possible that now it recognizes the fourth drive as sdb and so the first one gets to be sdc and my system drive moves to sdd as it is the second drive?
after reading this i'm not being clear, but i dont how to explain better.. :( 
so my next step was to, again, edit grub options form the grub screen and leaving it as (1,1) as its the only one that did something so i think thats correct, i tried to change my kernel image link, from /dev/sdd3 and it seemed to worked out but in one point it started to fail and scaped to console with several errors, and if this is really correct as it seems correct, if the system has change my de from to sdc to sdd and the system is looking for sdc ti seems logical that it will not find system iles in sdc as it not anymore the system drive? is this correct? if not, what can i do, why i cant get my system to start? and if i am correct what should i do? switch my fisrt drive whit my second one in order to let it be sdc???

please if someone can help me it would really appreciated.. :P
PD: i tried the new drive in windows and it works perfect, and i also have fomatted it in ext3 system as i may need it readable from windows. :)

---

### Post by MasterHead on 2006-09-07
so, if i'm correct withe the change of dev, would this be the solution? :

change sata cable from first drive to second, and viceversa, so the system drive stills as dev/sdc and in grub change (1,1) to (0,1) as it would now be the first drive?

---

### Post by MasterHead on 2006-09-08
hi agian, well after all i achive to fix it .. :)

yesterday trying to fix it i conneted the fourth drive and in grub set to start from /dev/sdc3 instead of /dev/sdb3 and ¡surprise! it worked out, but when checking file systems it broke down again as it was trying to check /dev/sdb3 filesystem instead of /dev/sdc3, so i switch sata cables until my system drive got to be sdb again and now it works perfect, only had to reasign drives in fstab and thats all.. :)

what i dont really get is why it has to change my drives assignment when i add a new drive... ¿? but knowing it theres no prob as i can fix it just trying... :)

Thanks everybody.. :)

---

