---
title: "Help! having big trouble deleting Ubuntu Partitions!"
date: 2009-03-13
forum: General Help
---

### Post by solorize on 2009-03-13
HI

I am currently having a problem deleting partitions that
Ubuntu and Xubuntu have made on my HDD.

I started off with just Windows 2k on my HDD and then decided to
install Ubuntu. After managing to mess up GIMP I decided to get rid of Ubuntu and then try Xubuntu. I booted up from the Xubuntu ISO on cd, and then selected Install.

When I got to the Partition section, I then selected Manual
and deleted the partitions to only leave the NTFS (which I guess
is Win 2k), but then when I tried to click the [Finish] button it
came up saying something like “no root.. please correct this in Partition program”, sorry I cant remember the whole message, but it was along those lines.

I then went back to the partition screen, which still showed all the partitions! & repeated the deletion process I had previously done, but then this time I chose [Quit].
Then rebooted and selected Install again, and when I got the the Partition part, all the partitions where still there again!. So I decided to just install Xubuntu anyway..


After playing around with Xubuntu for a while I decided that I prefer the way Ubuntu works and looks, so repeated the process of trying to delete the partitions partitioning and reinstalling. 

Now I have about 7 partitions on my HDD and cant get rid of them !!.

Also when I boot and GRUB loads I have 4 different OS’s to boot into.

If anyone knows how to get rid of all the non Windows partitions,
I don’t mind loosing all the Ubuntu partitions and then reinstalling a fresh copy back on, I would be very grateful as its driving me mad.


Regards

Mark

---

### Post by heindsight on 2009-03-13
Boot into the ubuntu installation you're using at the moment, open a terminal window, run the following commands and post the output here please.

```
mount
sudo fdisk -l
```

---

### Post by indytim on 2009-03-13
Yikes!

The reason the partitions are still there is because you have not finished the install.

I'm assuming from wading through your tale that the end result is that you want to have one installation of Ubuntu and the Windows ops.

Here's my short recommendation to get to that point in the universe:
1.  Get a copy of GParted Live, burn as an iso to a bootable CD.
2.  Boot to GParted Live and delete the Linux partitions that you have created.
**3.  Exit GParted and IMMEDIATELY boot to the Ubuntu Live/Install CD.**
4. When it comes time to do the partition selection, you can choose to use the available unallocated space as an option or do the manual partition.

The reason #3 is so important is that by deleting the ext3's, you will have also removed the GRUB boot loader, thus you will temporarily have lost the ability to effectively boot via GRUB.  This capability will be restored after you go through the re-installation of Ubuntu.

Hope this helps clarify things for you.

IndyTim

---

### Post by markusf21 on 2009-03-13
gparted is also on the Ubuntu live cd under system/ admin

---

### Post by nelskurian on 2009-03-13
someway late.....

If your previous ubuntu installation still active then goes to terminal and 

#sudo fdisk -l
It shows all the partitions....
If  none of your linux installation working..then reboot the machine with boot cd and then manually deleate the linux partitions and after that waht error message do you got?...Then create the partitions for the xubuntu.Create / and 'swap' partitions.then go through....
needs reply..

---

### Post by solorize on 2009-03-13
Thanks to everyone who has replied :)

I took "indytim's" advice and ran Gparted
and deleted the Partitions and then re-installed
Ubuntu, and it has worked a treat :D

Thanks again for all your help ppl.

Regards

Mark

---

