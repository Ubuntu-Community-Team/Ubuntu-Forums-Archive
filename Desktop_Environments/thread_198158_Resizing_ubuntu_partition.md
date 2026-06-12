---
title: "Resizing ubuntu partition"
date: 2006-06-16
forum: Desktop Environments
---

### Post by kin242 on 2006-06-16
Hello

I have UBuntu dapper drake 64bit (gnome) on my second hard drive. I now boot straight into grub on that drive which offers me the choice between booting into windows (on Drive 1) or Ubuntu.
I'd like to also install Kubuntu and Suse, so I can choose between the all at boot. I know I need to partition my drive properly to do this but at the moment it wont let me because it's all ubuntu's drive.
How can I resize my ubuntu partition, shrink it to a third of the disk (or a bit less) and put 2 other reiser partitions in which I can use for Suse and Kubuntu without losing my current ununtu installation?

Also, should I fiddle with grub or anything or will it find them on its own once I install them?

Any help much appreciated! :D 


Karl

---

### Post by andrewpmk on 2006-06-16
[QUOTE=kin242]Hello

I have UBuntu dapper drake 64bit (gnome) on my second hard drive. I now boot straight into grub on that drive which offers me the choice between booting into windows (on Drive 1) or Ubuntu.
I'd like to also install Kubuntu and Suse, so I can choose between the all at boot. I know I need to partition my drive properly to do this but at the moment it wont let me because it's all ubuntu's drive.
How can I resize my ubuntu partition, shrink it to a third of the disk (or a bit less) and put 2 other reiser partitions in which I can use for Suse and Kubuntu without losing my current ununtu installation?

Also, should I fiddle with grub or anything or will it find them on its own once I install them?

Any help much appreciated! :D 


Karl[/QUOTE]

First, I STRONGLY RECOMMEND that you back up all your files in /home before you make any modifications to your partitions. If you wish, you can back up / but it isn't really necessary because the partition editor *should* preserve your data.

If you want to resize your Ubuntu partition(s), you must unmount them first, which may make gparted inoperable. I STRONGLY RECOMMEND that you use the Ubuntu Live CD - GParted is installed on it.

On the Live CD, run gparted. It will allow you to resize your partitions without deleting their contents. I hope you backed up your files in case there are any problems. Click Edit > Apply and pray. Now you are ready to install your new distributions.

As to GRUB configuration, I'm sorry but I don't know the answer to that question.

---

### Post by Herman on 2006-06-16
Try [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), that's the easiest way to do anything with our partitions, and it's free, and it's only a small download. It is not necessary to unmount partitions when you use the GParted LiveCD because the GParted liveCD  mounts them as 'fakeraid' (or something like that). Or, you should be able to use GParted on the 'DesktopCD', as andrewpmk suggested, I haven't tried that yet.

Your Suse and Kubuntu installations will also offer the GRUB bootloader. If you also install GRUB with those, will automatically detect your existing Ubuntu installation and each successive GRUB configuration will add the ones before it. 

If you want to be double-safe, you can also install GRUB to your first sector of your Ubuntu partition (as well as MBR), ```
sudo grub-install /dev/hdb1
```(Where hdb1 is your Ubuntu partition). Then if anything does go wrong you can still boot with [GAG Boot Manager]("http://gag.sourceforge.net/"). Here's how, [*click here*]("http://users.bigpond.net.au/hermanzone/p12.htm").

When you are making all your partitions, remember you can have four primary partitions or three primary ones with one called 'extended'. The 'extended' one can contain as many 'logical' partitions as you like as long as they are strung together in a series, ('contiguous'). They can have gaps of free space in between, but no primary partition can interupt the string of 'logical' partitions or it will break the chain and make some of them unuseable. TIP: It's easier to just make all your partitions 'logical'.

Regards, Herman :D

---

### Post by kin242 on 2006-06-17
Thank you very much for all your help.

I resized the partition using the ubuntu live CD and gparted. It resized it fine. I have now installed Suze and that works fine although I had to manually add a line in the GRUB because Suze did not install its own grub/did not add itself to the list. Anyway it was quite simple to do.

I shall shortly be adding kubuntu.

Once again, thank you!!

---

