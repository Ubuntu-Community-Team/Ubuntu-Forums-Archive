---
title: "Requesting assistance in dual-booting Ubuntu and Win"
date: 2005-06-26
forum: Desktop Environments
---

### Post by cajunaggie on 2005-06-26
Forgive a n00b his ignorance (and the irresistible 1337-speak). I'm currently running Ubuntu 5.04 Hoary Hedgehog and it works just fine except for some issues with Audacity, but that's another post. However I miss my old games dearly (Ah *Alpha Centaurai* how I love you so) and, from what I have read on the subject, I have neither the brains nor the patience to get WINE up and running.
I'd like to dual boot Ubuntu with Windows 95 or 98, assuming I can get my hands on a copy. All my games can run on 95 if need be, so I don't need the latest greatest version of Windows.
Now, assuming I can find Win95/98, how I do I go about dual booting. I've been told that I'll have to move my Ubuntu to the second partition, because Win has to be on the first. What do I do after that?

---

### Post by richburr on 2005-06-26
If you're talking about reinstalling Ubuntu, then it's easy.

You'll want to partition your drive, and then install Windows in a FAT partition (you could do the partitioning with a DOS boot disk with DOS fdisk, or a Linux live/rescue CD like Knoppix). You want to at least create the FAT parition, you can leave the rest of the space free and set it up during the install if you want.

Then install Ubuntu, and when it asks about partitioning drives say that you want to do it manually. Add whatever Linux paritions you want.

When Ubuntu sets up the GRUB boot loader, it should automagically add an entry for booting Windows. It did that for me with XP.

Hope this helps.


Rich

---

### Post by cajunaggie on 2005-06-26
Thanks. I'll probably end up doing that. But just in case I decide to get creative is there a way to move my existing version of Ubuntu (edits, tweaks and all)  from the first parition to the second partition?

---

### Post by Martin Witte on 2005-06-26
That depends a bit on the size of your hard disk. If you have enough space left it is possible. 

First take a backup of all your own data.
Now boot with e.g. Knoppix or another bootable Linux cd.
Resize your Ubuntu partiiton - to the size you want your Windows partition  to be.
On the now available space you create a new ext3 partition. 
Mount both partitons and use cp to copy your data from the first to the seconfd partition, I think a cp -drP command will do.

You get your windows disk - and install it in the first partition.

Now boot again with the bootable Linux cd, and install grub, first mout the Ubuntu partition, then start grub with ' grub --configfile=/mnt/ubuntu/boot/grub/menu.lst. if your seconf partion is dev/hda5 then type in grub root(hd0,4) -- grub starts counting at zero, partitions start at one, so in grub the number is one less -- the type setup (hd0).

Now boot again - if all well you boot into Ubuntu.

Edit /boot/grub/menu.lst, add here :

timeout 5

and to the end:

title Windows
root (hd0,0)
makeactive
chainloader +1

If you now boot you should see a menu with options for Ubuntu an for windows.

I did not test all of this this recipe, but I played a lot with grub,  - additions/remarks are more than welcome

---

### Post by miscz on 2005-06-26
[QUOTE=cajunaggie]Ah *Alpha Centaurai* how I love you so[/QUOTE]

[Alpha Centauri](http://www.lokigames.com/products/smac/) was ported to Linux.

---

### Post by richburr on 2005-06-27
[QUOTE=Martin Witte]
I did not test all of this this recipe, but I played a lot with grub,  - additions/remarks are more than welcome[/QUOTE]

That looks pretty accurate to me.

The Ubuntu install is so fast and easy that I would probably just go that route myself, but I'm lazy :)  You could always back up some things like your home directory in advance if there is data you don't want to lose.

But if you have spent a lot of time customizing your system, it might be worth it to work through copying the files.


Rich

---

