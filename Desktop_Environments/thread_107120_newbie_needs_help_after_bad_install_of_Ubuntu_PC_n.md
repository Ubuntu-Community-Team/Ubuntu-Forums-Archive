---
title: "newbie needs help after bad install of Ubuntu PC not booting"
date: 2005-12-22
forum: Desktop Environments
---

### Post by dteckie on 2005-12-22
Help!!!  Newbie screwed up big time.  I have old pc 1.1 ghz AMD duron cpu and 2 HD's 30 G and 80 G . Had win xp working fine loaded on boot drive c : used partition magic in Windows to partition 2.5 G free space to install and play around with Ubuntu linux. Made a swap file partition 560 Megs and the rest free space to install Ubuntu. All was going well after an hour or so Ubuntu gave me an installation error. I rebooted my PC into windows and using partition magic made the Linux partiton larger to 5G thinking maybe the intall error was due to not enough space to install ubuntu.Then tried to reinstall ubuntu and error message again no install. Then I stupidly deleted the linux partition and tried to dlete the swap partition . Partition magic deleted the linux partition but not the swap. Now the swap file is only 30megs and PC will not boot up I get a Grub not found error. We know We screwed up but how do I at least get win xp working again. Second is there a way to get rid of the swap partiton I made and is now bad????

---

### Post by mtron on 2005-12-22
ok, well, fist suggestion: Ubuntu comes with a very good partitioning tool during install. just read the provided help it's awsome.

Next: check your grub Windows boot settings. it should use something like (assuming you have the windows install on the fist partition of the first drive:

title		WinXP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1


when you try to reinstall ubuntu, use the normal method ti'll the partitioner pops up, then select "manually edit partitioning table", delete the previous Ubuntu and swap partition, that the partitioner displays "free space", afterwards select the free space and use the option, "partition free space automatically. Now ubuntu will partition the free space. That''s the most failsafe method and it works 100%

cheers

---

### Post by dteckie on 2005-12-22
[COLOR="Red"]ok, well, fist suggestion: Ubuntu comes with a very good partitioning tool during install. just read the provided help it's awsome.[/COLOR]

OK I'm a newbie how do I get to Ubuntu help can you walk me through the check of the grub ?? I think I may have destroyed it when I tried to delete the swap space. Win XP is installed in first partition. As it stands now there is only win xp partition and a small swap partition. Cannot make new partition to install OS nor can I change/delete the swap partition in Ubuntu.



Next: check your grub Windows boot settings. it should use something like (assuming you have the windows install on the fist partition of the first drive:

title WinXP Pro
root (hd0,0)
savedefault
makeactive
chainloader +1


[COLOR="red"][COLOR="Red"]when you try to reinstall ubuntu, use the normal method ti'll the partitioner pops up, then select "manually edit partitioning table", delete the previous Ubuntu and swap partition, that the partitioner displays "free space", afterwards select the free space and use the option, "partition free space automatically. Now ubuntu will partition the free space. That''s the most failsafe method and it works 100%[/COLOR][/COLOR] 

I tried to delete the swap partition but it gives me error and does not delete it. Can I make the sawp partition larger with the Ubuntu partition ??/ I tried and does not change size maybe I'm not doing it correctly!!!!
 I think I need someone to walk me through this. Since I can only boot from CD and need to partition and free space on HD.

---

### Post by mtron on 2005-12-23
I recomment that you use the wiki at [http://wiki.ubuntu.com](http://wiki.ubuntu.com), a quick search fires up 

[https://wiki.ubuntu.com/Installation/I386?highlight=%28install%29](https://wiki.ubuntu.com/Installation/I386?highlight=%28install%29)
[https://wiki.ubuntu.com/CommonProblemsInstall?highlight=%28install%29](https://wiki.ubuntu.com/CommonProblemsInstall?highlight=%28install%29)

some help on the boot loader grub: 
[https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29)
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

and finally the partitioning tool:
[https://wiki.ubuntu.com/forum/installation/Partitioning?highlight=%28partitioning%29](https://wiki.ubuntu.com/forum/installation/Partitioning?highlight=%28partitioning%29)

do not use 3rd party partitioning tools from windows use the tool during the ubuntu install, don't worry if you follow the steps everything will be fine afterwards! 

If you need more real time help i recommend joining us at the channel #ubuntu on irc.freenode.net

---

### Post by Sef on 2005-12-27
Go to Herman's site: he has the complete install with pics.

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

