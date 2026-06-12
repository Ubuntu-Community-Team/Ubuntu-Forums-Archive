---
title: "repartition with gparted live cd"
date: 2009-03-11
forum: General Help
---

### Post by mrpind on 2009-03-11
i am dual booting XP and Ubuntu 8.10. i need more space for XP and am using gparted live cd to make more space. I can shrink Ubuntu's partition, but i cannot add to the windows partition. i dont know why it won't add the space, can someone please help.

---

### Post by taurus on 2009-03-11
Is Ubuntu partition a primary or logical partition?  Post a screenshot of gparted if you want, Applications -> Accessories -> Take Screenshot.

---

### Post by mrpind on 2009-03-11
i'm not sure if its a logical or primary partition. how can i find out? i attached a screen shot of gparted.

---

### Post by taurus on 2009-03-11
Okay, a couple of problems (or maybe more).  First, you cannot resize Ubuntu, /dev/sda5, while you are using it.  That's why you see the lock in front of root partition.  You have to do it from either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Second, Ubuntu root partition, /, is on logical partition, /dev/sda5, so you need to shrink it as well as the extended partition, /dev/sda3.  Then, expand windows partition, /dev/sda1, to cover that unallocated space ASSUMING that /dev/sda1 is right next to the extended partition.  

Again, you have to do all these from the LiveCD.

And before you reboot with Ubuntu LiveCD, let's see exactly where /dev/sda1 is.

```
sudo fdisk -lu
```

---

### Post by mrpind on 2009-03-11
i took a screen shot of the terminal with the command you gave. i really appreciate this help. thank you so much.

---

### Post by mrpind on 2009-03-12
i tried to resize the extended partition, but it would not let me shrink it even after i shrunk the dev5 partition. is there any way that i can just get rid of the ubuntu partition and give all the space to XP and then reinstall Ubuntu?

---

### Post by taurus on 2009-03-12
Did you do all the from Ubuntu LiveCD?  Don't forget to unmount the swap partition (highlight the swap and click the right button of the mouse --> swapoff) if it's mounted.

---

### Post by mrpind on 2009-03-12
i did all the partition stuff off of the dparted live cd. i can resize /dev/hda5, but not /dev/hda3. i made sure that the swap partition was swapoff. the is a flag "boot" by the /dev/hda1 partition, is that of concern? thanks for your help.

---

### Post by taurus on 2009-03-12
Maybe a new screenshot of what you have done so far.

---

### Post by mrpind on 2009-03-13
i havent changed anything yet since i cant shrink the /dev/hda3 and make the windows partition larger. do you know why i wouldnt be able to shrink the /dev/hda3 partition? i've shrunk the /dev/hda5 partition and an unallocated space shows up on gparted, but i cant give that space to the windows partition or shrink the /dev/hda3 partition even after i make an unallocated space.

---

### Post by meierfra. on 2009-03-13
Make sure that you shrink the Ubuntu partition from the front, so that the newly create  unallocated space is in front of the Ubuntu partition ( and not between the Ubuntu and swap partition). Also you should backup all your valuable data before doing any repartitioning.

---

### Post by mrpind on 2009-03-14
thank you very much for that advice. i shrunk it from the left side and it worked. i did not think that would matter. i was able to repartition, but an unallocated partition was created that i did not ask for. is this of concern? i attached a screenshot of the new partitions.

---

### Post by meierfra. on 2009-03-14
> i was able to repartition, 
Great.

> but an unallocated partition was created that i did not ask for. is this of concern? 

No. gparted keeps all the partitions on cylindrical bounds. So it's quite common to have some unallocated space of size less than 8MB.

---

### Post by mrpind on 2009-03-14
thank you for your help. i really appreciate it. and i have one more thing i'd like to know. i want to downgrade from 8.10 to 8.04. can i just use the 8.04 cd i have and reinstall and it will completely remove 8.10? or is there an easier way?

---

### Post by meierfra. on 2009-03-14
> can i just use the 8.04 cd i have and reinstall and it will completely remove 8.10? 

Yes. Choose manual partitioning and use your current ubuntu partition for the "/"partition.

> or is there an easier way? 

I don't think so. But I'm not an expert in this matter.

---

### Post by mrpind on 2009-03-16
when i select manual partitoning, it gives a list of partitions to choose from. i click on the 8.10 partition and i can edit it. but in the edit window, i can choose to format the partition as a type. which should i choose?

---

### Post by meierfra. on 2009-03-16
"ext3"

---

### Post by mrpind on 2009-03-16
when i select edit partition, it has a "use as" and the option for ext3 says "ext3 journaling file system." is that of concern or is it supposed to say that? and should i just select that?

---

### Post by meierfra. on 2009-03-16
That's what it is supposed to say.

---

### Post by mrpind on 2009-03-16
i didnt want to do anything before asking. thank you very much for your help.

---

