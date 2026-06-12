---
title: "format second Drive"
date: 2009-01-20
forum: General Help
---

### Post by zcartist on 2009-01-20
I have 2 300gb HDDs The Drive I installed ubu 8.10 on is ok. Somehow I got 2 partitions on the second one 1 only has lost and found on it so I can't access it. Gpart wont let me resise it either. Can I get a walkthrough on reformatting the second drive?

---

### Post by dcstar on 2009-01-20
> **zcartist said:**
> I have 2 300gb HDDs The Drive I installed ubu 8.10 on is ok. Somehow I got 2 partitions on the second one 1 only has lost and found on it so I can't access it. Gpart wont let me resise it either. Can I get a walkthrough on reformatting the second drive?

Simply unmount it first.

---

### Post by zcartist on 2009-01-20
Cool thanks my friend

---

### Post by scouser73 on 2009-01-20
> **zcartist said:**
> I have 2 300gb HDDs The Drive I installed ubu 8.10 on is ok. Somehow I got 2 partitions on the second one 1 only has lost and found on it so I can't access it. Gpart wont let me resise it either. Can I get a walkthrough on reformatting the second drive?

You need to have **Gparted** installed firstly. so go to **System**, **Administration**, **Synaptic Package Manager**, in the search box type **Gparted** and install it.
 
Unmount the drive first by placing the cursor over the drive and scrolling down to [B]Unmount Volume

[/B]Once Gparted is installed go to **System**, **Administration** & scroll to **Partition Editor**, then select the drive you want to format. Click **Device**, click **Create Partition Table**, that will delete the information that is stored on the drive. 

Then click **Partition**, and select **Format To**. You can then select the type of file system you want, once you have done that then click **Apply** and the formatting will take place.

I would suggest that you choose either **EXT2** or **EXT3** for your file system.

---

### Post by zcartist on 2009-01-20
Thanks  I did everything but create the table.I just deleted a partition and stretched the other .still not sure why it doesn't automount. It would be nice to have it part of the file system. Or was that why I should format
the whole thing...should I start over?

---

### Post by todak on 2009-01-20
[https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20A%20Mount%20Point) should get you going.

---

### Post by zcartist on 2009-04-27
Fresh install of Jaunty,,,created table on second drive & formatted to. Drive is in the places pulldown menu at start up with lost and found on it...no access. If I unmount, it's nowhere to be found until a restart. Any help is welcome.

Thanks

---

### Post by zcartist on 2009-04-28
FAT 32 seems to have done the trick but all others didn't take

---

