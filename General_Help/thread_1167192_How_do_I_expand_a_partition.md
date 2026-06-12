---
title: "How do I expand a partition?"
date: 2009-05-22
forum: General Help
---

### Post by Bigtime_Scrub on 2009-05-22
I duel boot Vista and 9.04 Ubuntu. When I first installed, I did a volume shrink in Vista and then installed Linux on the available space that was left. 

Now I want to keep Vista, but I want Ubuntu to take a larger piece of the hard drive. I want Vista to go down to 20 GB (it has 70 GB right now) and I want Ubuntu to take the rest. (Ubuntu has 40 and I want it to take 90).

How can I do this? Do I go into Vista and do a volume shrink again and then work in fdisk or gparted to try and get the rest of the unallocated space or can I just go into fdisk and tell it to expand? I do not want to damage my vista install.

---

### Post by Bender2k14 on 2009-05-22
How did you do the "volume shrink" in Vista?

[QUOTE=Bigtime_Scrub]Do I go into Vista and do a volume shrink again and then work in fdisk or gparted to try and get the rest of the unallocated space or can I just go into fdisk and tell it to expand? I do not want to damage my vista install.[/QUOTE]

Yea, that is how I would do it.  I usually use [Partition Magic]("http://en.wikipedia.org/wiki/PartitionMagic") to shrink the Windows partition and then use Gparted inside Ubuntu to grab the unallocated space.

---

### Post by ibuclaw on 2009-05-22
Can you resize the Vista partition while in Vista? If so, do it. It will probably be a far safer option to let Vista to resize itself.
After Vista has finished resizing itself, insert the Ubuntu LiveCD into the CD/DVD Rom drive, and reboot to boot into the LiveCD.

When the Ubuntu LiveCD logs in, Go into **System -> Administration -> Partition Manager**
Then select the Ubuntu Partition and you should see a button, "**Resize/Move**", click it, then a new window will open where you can grab the edge of the partition and enlarge it across the empty space to fill it (graphically speaking).

Then click **Apply** and wait for the changes to complete.

Regards
Iain

---

### Post by Bigtime_Scrub on 2009-05-22
Ok I'll do that. 

When I installed I went into Vista and 

Administrative Tools -> Disk Management -> Partition

and then click on Shrink Volume where you set the partition size in Mb. What will happen is in Vista it will show a space on the hard drive that is unallocated.

---

### Post by Bender2k14 on 2009-05-22
Sweet, that is great that Windows Vista supports partition resizing.

[QUOTE=tinivole]When the Ubuntu LiveCD logs in, Go into System -> Administration -> Partition Manager[/QUOTE]

On the Ubuntu LiveCD of 9.04 Jaunty, the menu item is called "Partition Editor".  Also, if there is no menu item in the list about partitioning, first check if it is just disabled (by looking in System->Preferences->Main Menu).  If it is there, you can get it to appear in the menu by checking it.  Otherwise, installing gparted (with the following command) will get the menu item to appear.

```
sudo apt-get install gparted
```

---

