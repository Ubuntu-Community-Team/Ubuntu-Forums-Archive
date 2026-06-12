---
title: "Formatting USB drive"
date: 2007-06-08
forum: Desktop Environments
---

### Post by elenius on 2007-06-08
Is there a graphical tool to format drives? I would like to just be able to right-click on my USB drive and chose "Format". I can figure out how to do it from the command line, but new windows converts might not. I would almost consider this a bug...

Sorry if this has been covered before.

---

### Post by jim_p on 2007-06-08
Well... I know it will sound like the most stupid idea ever...
but when I want to format my usb stick or memory cards I launch Gparted,
select the drive from the drop-down list on the top left corner,
right click -> unmount drive and right click again -> format to... fat32

In the same way you can use the Disk Management tool under System > System administration > Disks,
select the drive from the list on the left, go to the "Partitions" tab, click "Unmount drive" and click Format afterwards.

Excuse me for any wrong translations of the menus.
I am using Ubuntu 6.06 LTS in Greek. :???:

---

### Post by coffeecat on 2007-06-08
Are you using Ubuntu or Kubuntu? Download and install Gparted (gnome) or Qtparted (kde) from the repositories. That will format and partition any internal or external drive, including usb ones.

No, you can't just right-click and format. Can you do that in Windows? I hope not - it's far too potentially destructive to be so easily accessible. I would consider that to be a major and disastrous bug if you could.

Once you've installed Gparted, go to System > Administration > GNOME Partition Editor. I don't know where Qtparted would appear in the KDE menu, but it wouldn't be hard to find.

---

### Post by jim_p on 2007-06-08
I am using Ubuntu and Gparted (Gnome enviroment in both).
When I say "right click -> unmount drive and right click again -> format to... fat32" I mean inside Gparted!!
A drive has to be unmounted to be formated. Sorry for any misunderstandments :( 

PS. I checked my Gparted method 10 minutes ago and formated my CF card to fat32 and an error popped up :(  so i did the same through disk management in vfat and everything went ok. What is vfat?!?!

---

### Post by coffeecat on 2007-06-08
> **jim_p said:**
> I am using Ubuntu and Gparted (Gnome enviroment in both).
When I say "right click -> unmount drive and right click again -> format to... fat32" I mean inside Gparted!!
A drive has to be unmounted to be formated. Sorry for any misunderstandments :( 


Of course you have to unmount a drive/partition before you can format it. Since you have Gparted already and can right-click on a partition in Gparted to do everything you want to do, I don't understand the point of your post. :?

> **jim_p said:**
> What is vfat?!?!

[Link.](http://en.wikipedia.org/wiki/VFAT)

---

### Post by jim_p on 2007-06-09
> Is there a graphical tool to format drives? I would like to just be able to right-click on my USB drive and chose "Format"

That's why i suggested Gparted or Disk management. Graphical interface.

---

### Post by coffeecat on 2007-06-09
**jim_p**, I apologise for the first part of my post. It was late where I was and I thought you were the OP. Of course your post had a point. I'm sorry.

---

### Post by jim_p on 2007-06-09
It's ok mr. cofeecat! I was not offended.

I still wonder why Gparted gave me an error. Using disk management I had no problems at all and my CF card was instantly recogniosed by the camera and xp.

Excuse me for the delay but I check the forums... once i remember :(

Have a nice day

---

