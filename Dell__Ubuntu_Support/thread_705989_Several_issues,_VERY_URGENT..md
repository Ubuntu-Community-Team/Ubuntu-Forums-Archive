---
title: "Several issues, VERY URGENT."
date: 2008-02-24
forum: Dell  Ubuntu Support
---

### Post by Xanderg on 2008-02-24
I have been battling Ubuntu all day and I don't hate it yet, but I would like to settle a few things before I make my decision on it.  First of all.

I'm running Ubuntu 7.10 I believe and here are my issues with Ubuntu:

I have no sound.  This is the error I get:
"No volume control GStreamer plugins and/or devices found."

Secondly I set up my external to serve as a back up, as far as I was aware it was capable of being read (it is NTFS) however it won't even be read.

Now, I also set up my HDD in partitioned sections so I may re-install Vista/XP however it won't let me.

As I get to the set-up screen where it asks me to select a partition I see no partition, not even the primary HDD itself, and then the system gives me a BSoD.

This is very urgent.  I was hoping things wouldn't become so uncontrollable.  The biggest issue is that I forgot to check and see if my printer was compatible and low and behold it isn't.  I need this settled fast, I have several important documents due soon and if I can't even access them I'm not sure what I could do.

---

### Post by justin whitaker on 2008-02-24
> **Xanderg said:**
> I'm running Ubuntu 7.10 I believe and here are my issues with Ubuntu:

Since you are in the Dell Forum, how about you tell us which Dell it is?

> I have no sound.  This is the error I get:
"No volume control GStreamer plugins and/or devices found."

Here is a detailed work around for that:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

> Secondly I set up my external to serve as a back up, as far as I was aware it was capable of being read (it is NTFS) however it won't even be read.

Gutsy has Read by default. If you can't read it, you may need to add the NTFS configuration tool (it is in add/remove), and if you want to use it as a backup, you should probably install ntfs-3g.

> Now, I also set up my HDD in partitioned sections so I may re-install Vista/XP however it won't let me.

As I get to the set-up screen where it asks me to select a partition I see no partition, not even the primary HDD itself, and then the system gives me a BSoD.

What are the partitions formatted as? Vista and XP will see all FAT and NTFS partitions, and have them listed in case you want to format them. The fact that you don't see them makes me wonder if they are formatted correctly.

> This is very urgent.  I was hoping things wouldn't become so uncontrollable.  The biggest issue is that I forgot to check and see if my printer was compatible and low and behold it isn't.  I need this settled fast, I have several important documents due soon and if I can't even access them I'm not sure what I could do.

You can always use the LiveCD, put the documents up on Google docs, and go to Kinkos, or some other print shop. 

What I would do, in your case, if back up the important files (to the external drive, or a DVD), and then reinstall Vista, then install Ubuntu.

---

### Post by ChaosParser on 2008-02-24
> **justin whitaker said:**
> 



What are the partitions formatted as? Vista and XP will see all FAT and NTFS partitions, and have them listed in case you want to format them. The fact that you don't see them makes me wonder if they are formatted correctly.



That's not always true.  A lot of the time the XP cd will see a filesystem it doesn't recognize and then refuse to admit that you have a hard drive, let alone partitions.  I've seen it happen rather frequently. 

To the OP:  Never install Linux and THEN install windows.  Always install windows first.  Linux can adapt.  Windows, not so much.

---

### Post by SmallFish on 2008-02-25
> **ChaosParser said:**
> That's not always true.  A lot of the time the XP cd will see a filesystem it doesn't recognize and then refuse to admit that you have a hard drive, let alone partitions.  I've seen it happen rather frequently. 

To the OP:  Never install Linux and THEN install windows.  Always install windows first.  Linux can adapt.  Windows, not so much.

Agreed with this. Always load your windows first then linux and use grub to control your booting. Since you have some weird issues, I would start over from formating your hd (plan ahead) , install windows then ubuntu. I have done this in 3 desktops and 2 laptop without any issues that you have mentioned. 1 of the laptop dated back to year 2000 build , it's toshiba 1605 :)

---

