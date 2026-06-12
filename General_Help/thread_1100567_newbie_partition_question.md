---
title: "newbie partition question"
date: 2009-03-19
forum: General Help
---

### Post by thundaraptor on 2009-03-19
HI all, I tried to follow the instructions to shrink my vista partition but i am getting the "0" available to shrink options.  Any ideas or suggestions on other ways to accomplish this?

---

### Post by ivanvajar on 2009-03-19
This is NTFS partition we are talking about? Did you check it for errors? Ubuntu will not shrink your partition if it has errors on it. So, from Windows =>

Right click the partition/tools/check for errors and make sure you enable full scan. It will perform scan after reboot.

---

### Post by Technoodle on 2009-03-19
Are you using Vista itself to shrink the partition or using a live CD?  Vista will not shrink the primary boot partition very well because the page file and shadow copy file(s) cannot be moved by Vista.   A Live CD should not have these limitations.  Partition Editor in Ubuntu should allow for a resize as long as there is available space.  As always, make sure you have a backup of any critical data before you do this.

---

### Post by thundaraptor on 2009-03-19
I am using vista itself and don't have a very good understanding of the partitioning process in general.  i have not installed ubunut yet, just using it for test off the cd.  what is a "Live CD"?  Thanks for the info.

---

### Post by ivanvajar on 2009-03-19
Yeah, don't EVER try to shrink partition if it's a partition you booted your OS from. I guess that I should have mentioned that you should use Ubuntu LiveCD to do all the partitioning you need instead of assuming you know that. Anyway, make sure your partition doesn't contain any errors or bad sectors and also defragment it before you do any shrinking.

---

### Post by ivanvajar on 2009-03-19
Live CD is that Ubuntu CD you have. Insert it in your drive, restart computer and start 'Try Ubuntu without any change to your system'

---

### Post by ivanvajar on 2009-03-19
After you started LiveCD, you'll find partition editor on your desktop. Run it and right-click partition you want to shrink. then => resize

1. Move the slider until you get about 20 - 25 GB of free space.

2. Right click new partition/create

3. Mark ext3 for filesystem

This will be your Ubuntu partition.

After you created ext3 partition, shrink it to create another partition **(linux swap)** that should be as big as your RAM memory is.

If you have **any** questions, ask. We don't want you to do something you are not sure about. We can take it step by step.

---

### Post by thundaraptor on 2009-03-19
ok invanvajar, looking at your post, if i use the ubunut cd that I made, i should be able to shrink the partition that windows is on, as long as I am working out of the ubunutu cd no problesm?  

what is the purpoe of making the linux swap partition and i thought I read that my system can only have 4 partitions.  right now my vista is showing c: 110 gb d: 1 gb and e: 1gb  won't this be too many partitions?  i don't even really understand why there are those small partitions.  

if I shrink the vista partition using ubuntu the data i have in windows shouldn't be erased right?  i have however made a backup.

---

### Post by ivanvajar on 2009-03-19
None of your data will be lost. Do you have any data on D and E partitions?

I have 6 partitions, so don't worry.

---

### Post by ivanvajar on 2009-03-19
Linux swap partition is something similar to swap space in Windows. It's not essential, but you should make it.

---

### Post by thundaraptor on 2009-03-19
nothing on any of the other data sources.  i have backed up all my data except outlook and firefox settings.  will maybe perform partition changes today.  difficult thought, maybe wait till sunday and have all day with laptop down.  very busy mba student so downtime is an issue but just really starting to hate vist.  thanks for information will put a post up after i try to partition.  thanks

---

### Post by estyles on 2009-03-19
One thing I don't see mentioned is that you can have only 4 PRIMARY partitions.  If you're installing Linux, especially as a dual-boot, then you can expect to want more than 4 partitions total, if not now, then at some point, so always create an "Extended Partition".  You can only create an Extended Partition if you have 3 or fewer primary partitions on the disk, because the extended partition counts as a primary.  Once you have an extended partition, you create logical partitions *inside* of the extended partition.

---

### Post by ivanvajar on 2009-03-19
Yup, this might be the reason thundaraptor mentioned '4 partitions thing'. Anyway, when installing Ubuntu, you go to manual configuration of partitions and give your ext3 partition mountpoint '/'

---

### Post by thundaraptor on 2009-03-19
i just followed all those directions, maybe i don't quite understand the statement about mountpoint '/' my system is shrinking the partition now and I think i have the other stuff done correctly.  not entirely sure if i did the logical partition right.  shouldn't matter too much as all data is back up cept for bookmarks.   will post again in a bit.

---

### Post by thundaraptor on 2009-03-20
i got the partition square away but i really don't understand how to mount the drive.  i think i need to do this to get ubunutu loaded correct?

---

### Post by Torquemada28 on 2009-03-20
No, mounting the partition before installing Ubuntu isn't required.
Just boot using your LiveCD and select the option to install Ubuntu. You can also select the option to run Ubuntu without changing the system as there will be an "Install" icon on the desktop once Ubuntu has loaded.
During the installation, you will be asked to select what partitions you want to install Ubuntu on. If you followed the previous instructions, you should have two new partitions; a large one and a small one. Select the large one to use the mountpoint "/" and the small one as "Swap". That might not make sense now but will be clearer when you get to that point in the installation.

Does anyone have a screenshot of the partitions page of the installer? That might help.

---

### Post by Torquemada28 on 2009-03-20
I tried unsuccessfully to find a screenshot of the partitions page of the installer. However, it did highlight one important piece of information that I missed. Look at the attached pic. When you get to that point in the installation, you should choose the "Manual" option. After that, you'll have to tell the installer that the new large partition is to mounted at "/" and the smaller one is "swap". At this point, you can also set Ubuntu to automatically mount your vista disk where ever you want but that can always be done later. Might be best not to confuse you further.
Unfortunately, using all these partitions makes installing Ubuntu hard for newbs. It's always easier to just use the entire disk and let Ubuntu automatically work out what partitions it needs and where.

---

### Post by ivanvajar on 2009-03-20
The thing is that you must specify mountpoint '/' for your Ubuntu partition during installation. You do this with manual configuration of HDD during installation. When you give mountpoint '/' to a partition, that partition becomes your Linux partition. It's as simple as that :-)

---

### Post by thundaraptor on 2009-03-20
i think then i didn't understand '/' as the mountpoint.  i don't understand anything about command interface or really what mounting is.  i did try using the install icon from the live cd but never saw the new smaller partition to install into so i am assuming i made a mistake somewhere in the '/' area.  also, windows doesn't recognize the new smaller partition, it just thinks my original large one shranke.  otherwise, thanks these posts are awesome and i am sure i will get through these little hurdles.

---

