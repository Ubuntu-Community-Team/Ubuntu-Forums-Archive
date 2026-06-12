---
title: "cant find partition"
date: 2008-12-22
forum: General Help
---

### Post by underwhelmed on 2008-12-22
Hi, I've finally sorted a rerasonable pc for dual booting.
yesterday i installed xubunto on an xp machine with 120gb hard drive. All went well; on boot i got an option screen to decide which system to boot to. very pleased.Xubuntu super quick. Had 100gb for xp and 15 for Xubuntu. (the other 5gb, well, who cares? acceptable loss).
so then i thought, why not reload the xp and see if i can speed that up a bit, spring clean and all that.
so, i stick in the the xp disk, all loads fab (and superquick). showed me 2 partitions, 1 big and 1 small, so bunged xp on the biggest. However on reboot no option for xubuntu.
Ho hum I think, why not just reload the ubuntu - tried that, it will install, but only inside the 100gb xp partition.  somewhere is my missing 15-20gb of space containing my xubntu boot up.
The bios still shows the disk size as 120gb, running the hard drive in another pc via usb only shows 1 100gb drive, vista disk management shows 2 partitions and free space - tried messing around with this and got the smaller drive and free space to merge, but got message saying that if i tried to delete it it may no longer be available. It did acknowledge that there should be a tottal of 120gb though.
then i put it all back in the original pc.  reloaded xp. it showed up as 2 partitions then, wow i thought.  loaded xp onto the larger and when i tried to relaod xbntu, you guessed it, still the option to load it only within the 100gb (now 95gb) partition only.
so, how to i get my 20gb back?
can i force a choice of a different partition during ubuntu set up?
If only i'd reloaded the xp first into the entire hard drive I wouldnt be writing this.
A total wipe of format to go back to one 120gb drive would do. no data to lose. I've only succeeded so far in re formatting/partitionning the 100gb bit and not merging it all together.
any tips gratefully received.
can find a thread on it - surely i'm not the first.
thanks

---

### Post by plucky on 2008-12-22
> so, how to i get my 20gb back?

When you install XP,it re-writes the boot loader in the MBR which pointed to the Grub menu that booted Xubuntu.

To re-write the MBR to enable Grub boot loader,use the Xubuntu Live CD and follow this [thread](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

For further information on Dual booting see the [Illustrated Dual boot site](http://users.bigpond.net.au/hermanzone/)


Good Luck

---

### Post by underwhelmed on 2008-12-23
Thanks for that excellent help; i expect one gets more fluent in finding the previous posts as timke goes on.

I think i'd managed to format the partition with the xubuntu on so the terminal command prompts didn't work BUT what you did do was push my in the right direction, thanks, namely to the live cd and to use the partition editor (applications-system-partition editor) which is brill!
what i did was to simply go device-create partition table [to erase the lot] then go to partition-new- whole disk as ntfs & primary partition.  Then I've reloaded windows (still going, it takes an age) with the intention of then subdividing the primary partition to fit ubuntu into just using the standard procedure on the live/install disk.

I'll report back if i'm not successful.

thanks for the advice.  I hope my tuppence worth may be of use to anyone else just starting out.

---

