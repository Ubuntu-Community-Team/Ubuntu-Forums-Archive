---
title: "How do i remove windows xp media center so i can lood ubuntu?"
date: 2009-04-03
forum: General Help
---

### Post by krine11 on 2009-04-03
Hi, I want to remove windows xp media center now since Ubuntu is AWSOME it is really fast and perfect for my computer. Can you please tell me how to unistall windows xp so i can both asve more space and also load with ubuntu with no fuss.

---

### Post by anjilslaire on 2009-04-03
Boot the Ubuntu cd, and run the installer. By default it will format the drive and install Ubuntu using the whole disk. Windows will be overwritten.

---

### Post by 3Miro on 2009-04-03
Now this kind of depends on how you installed Ubuntu and how you partitioned your HD.

If you installed Ubuntu from wibi (i.e. from within windows), I don't think you can remove windows. In either case a clean install would be preferable. (wait for a second opinion on this one, just in case, I have never used wibi)

If you installed Ubuntu on its own partition:

First back up all of your windows data that may be important, you don't want to loose family photos, music and such.

Second, load gparted from Ubuntu (you may have to add it form add/remove). When you start gparted, you should be able to see your current partitions.

Option one: format the Windows partition into ext2/3/4, whatever you use (default on 8.10 is ext3 and on 9.04 seems to be ext4). YOU DID BACK EVERYTHING UP, RIGHT? Now you have another partition that you may use to store music/ pictures/ movies/ whatever.

Option two: now this might be tricky. FIRST BACK EVERYTHING UP FROM ALL AND I MEAN ALL YOUR PARTITIONS WINDOWS UBUNTU OR WHATEVER. Then boot from the LiveCD and start gparted now you can delete the windows partition and expand the Ubuntu partitions at its expense. This depends on the physical orientation of your partitions. You can post a screen shot from gparted from within regular Ubuntu so we can see what can be done (and advice on options).

Option three: You can backup all your data from windows and Ubuntu and everything and make a clean Ubuntu install on the entire hard-drive. I would personally do that than resize partitions (resizing is risky, see the big sentence above), but that is just me.

---

### Post by brayden13 on 2009-04-03
Or just remove the entry for Windows on the GRUB boot loader list. You do it by going to 
```
sudo gedit /boot/grub/menu.lst
```

You will have to enter your password then Gedit will open and just go to the very bottom of the document and then remove the entry for Windows XP. Then download a partition software called GParted (it's free and opensource). Then format the Partition windows is installed in and format it to whatever format you want.

Now you are windows free! NOTE: before changing the menu.lst file i suggest you back it up incase you make a little mistake, it is very easy to mess up in that file but i've edited it a thousand times so if i haven't made a mistake yet i'm sure you wont'.

just remembered when gparted installs it installs into the System -> Administration -> Partition Editor.

FYI as the person above me suggested whilst i was writing this up if you installed it with "Wubi" then you cannot safely get rid of windows, To know if you installed it with Wubi try accessing your main windows partition. if you can you installed it the hard way if not then you installed it hte safe and easy way.

---

### Post by 3Miro on 2009-04-03
The only reason why you have not made mistake is probably because you alway had backups. ALWAYS make backups to system files that you will edit, it is just a good habit.

---

