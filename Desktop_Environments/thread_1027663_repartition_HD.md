---
title: "repartition HD"
date: 2009-01-01
forum: Desktop Environments
---

### Post by gusteman on 2009-01-01
Hi all you Ubuntu forum members. First of all let me wish you all a very happy 2009. Hopefully a year without troubles or problems.
For the time being I am using Gutsy on a Dell Optiplex GX1, Pentium III, 450Mhz, 256Mb SdRAM, 80Gb HD. I know it isn't really a performing PC but at this time I will have to do with what I've got.
I initially installed Feisty on a blank HD and wasn't really interested in partitioning it. So I gave all the space to Ubuntu. But now I would like to repartition it so that I have room for a Windows 98 OS that I have on CD. This should make it possible for me to play some of my favorite games (such as Sudden Strike I and II) when for the time being I have to do this on a separate PC. Anyone can give me some directions? Maybe an existing tutorial that I have not yet found? If it should be necessary to perform the repartitioning from a Live-CD I still have the Feisty Live-CD. Or if someone knows about a patch that would allow me to play the game in Ubuntu? Any of these solutions is very welcome:D
Thanks a lot for your time an interest.
Greetings, Gusteman

---

### Post by wmdiem on 2009-01-01
run gparted from a live cd. 
you will have to shrink the existing partition to create enough free space for 98 and it's apps, then make the free space a new partition. 
You might run into some issues with 98 not playing nicely with GRUB, but I don't know anything about this. 
I would definitely try to back up everything important before repartitioning the hdd.

---

### Post by kr1z on 2009-01-12
If you have mondo installed, and you don't want to start over with the setup you've already done, you can use mondo to back up the system that you have and (if all goes well) reinstall to a smaller partition after Windows install (which probably will overwrite grub in boot loader).  With Windows98, I suggest you aim for a small system partition like 2 GB and then use Windows98 fdisk to set up a separate FAT32 partition if you want a space that all OSes can read/write easily.  After that, you can set up the rest of your disk for one or more Linux distributions.

Knoppix has nice tools such as cfdisk, that will allow you to make changes in partitions easily.  If you install Windows98 and use it to create a FAT32 partition, you'll have hda1 and hda5 defined when you run cfdisk, and you can add hda6 for swap, hda7, etc. for Linux distributions.  After your partition changes are done, and everything is how you like it, use Knoppix again later to run tune2fs on the new Linux partition(s) to change maximum mount count to -1 (that is, no maximum) and check interval to 0 (that is, no check).

I've found that it can be a bumpy ride to reinstall from mondo on a HD that doesn't have a working Linux distribution with grub on the boot loader - you may find that you have to reinstall and do a lot of things over again.  Sometimes, but not always, a mondo install can put grub back in the boot loader.  If you are able to reinstall from mondo, you'll need to add an entry for Windows98 in menu.lst.

---

