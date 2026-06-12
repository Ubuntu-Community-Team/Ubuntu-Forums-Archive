---
title: "Deleted LINUX partition Grub Error 17 - Please HELP!"
date: 2006-09-10
forum: Desktop Environments
---

### Post by flub on 2006-09-10
Hi All,

I've just done something very very stupid. I removed the Linux from my old pc as I now have a nice new desktop for Linux, however the OLD PC was also my work Desktop which had a Windows XP Partition.

When I boot the old pc I get a Grub Error 17 as grub obviously got deleted!!!!!

Is there anyway I can recover the old pc so that it boots into Windows again.

Thanks in advance and I've learn a good lesson here!

---

### Post by smelly_sox on 2006-09-10
Hey Flub,
Don't panic. It's mostly harmless. grub is looking for itself, & I know that sounds reediculous, but only a small amount of code can be stored on a master boot record (MBR), the very start of a hard disc. What you need to do is reboot the machine with your Window$ XP disc inserted. Somewhere in there are options to fix, repair installation, Recovery Console maybe. At the console you need to type *fixmbr*. Reboot without XP disc in machine. It's all good.
Regards

---

### Post by glethro on 2008-07-16
hey id write this in a new thread bt for some reason im unable to post..

im a retard.. i was over tired and wasnt thinking and deleted the partion on my hdd with Ubuntu+Grub.. so now i cant get my comp to boot cuz theres no Grub :(

i do have a ubuntu live CD tht works and the comp will boot from it.. 

is there a way 2 fix this? smelly_sox recommened booting with the windows CD.. but my comp didnt come with it..

i have a Acer Aspire laptop, 2.4 dual with 32 bit os running windows vista premium.

thanks. any help is highly appreciated


---edit---
okay so i reinstalled ubuntu from the live cd and grub is working again. vista boots up :D
however i would like to remove ubuntu from my computer.. or at least resize its partion. Vista is only giving my the option 2 delete it.. which apparently doesnt work so well :P
if i was 2 either of these wt would i do?

oh.. and my comp has this acer recovery option that i can boot into from grub. (the cd might not be necessary?)

---

