---
title: "** Gparted Partition Resize **"
date: 2009-03-17
forum: General Help
---

### Post by MaximoMilkman on 2009-03-17
Hey guys I was wondering how i would go about resizing my windows partition with gparted.. It is formatted to NTFS so is there a way I can give more memory to it considering i dont download anything on UBUNTU i only need like 10 gigs right now it has 30 gigs and im running out of space on my windows partition! Thanks for the help! If you need anymore information i will provide you with it.

---

### Post by Therion on 2009-03-17
You'd just need to boot to a gParted LiveCD.  Then you would resize both the Ubuntu and Windows partitions as you wish.

---

### Post by MaximoMilkman on 2009-03-19
I went to the gparted live cd and i was able to resize my ubuntu partition to like 5GB but now i have like 33 gb of unallocated space.. i also could not make my NTFS windows partition grow? Is there a reason why? I would like to give the unallocated memory to the ntfs partition.

---

### Post by SikEnCide on 2009-03-19
you need to do this..

1. boot Ubuntu Live cd as it has Gparted on it.
2. open a terminal and type ```
sudo apt-get install ntfsprogs
sudo apt-get install ntfs-3g

```
3. run```
sudo gparted
```
4. Now extend the partition you want.

---

### Post by MaximoMilkman on 2009-03-22
So those commands above will allow my NTFS windows partition to be able to utilize the "Unlocated data" gparted now is showing?

---

### Post by SikEnCide on 2009-03-24
> **MaximoMilkman said:**
> So those commands above will allow my NTFS windows partition to be able to utilize the "Unlocated data" gparted now is showing?

Yes. Just to recap. You would like to extend the partition size of your windows NTFS partition right ?

If so Then these will indeed fix your problems.
What you are installing is support for NTFS. By default ntfs-3g should be installed. I had you run the commands just to make sure it is. The other part is what Gparted needs to partition NTFS.

After installing them make sure you launch Gparted with sudo privlages by using
```
sudo gparted
```

Then just tell it to resize the partition.

---

### Post by MaximoMilkman on 2009-03-24
Ok i did as above IT DOES let me resize my NTFS but only resizing it smaller not bigger. 

Screenshot below.. if link goes bad tell me i will reupload.

[http://www.picamatic.com/view/3012994_Gparter/](http://www.picamatic.com/view/3012994_Gparter/)

---

### Post by MaximoMilkman on 2009-03-25
Bump this thread... I really need help with this or I will be forced to format my HD and reinstall Ubuntu and windows.

---

### Post by alcahuete on 2009-03-25
The problem is that you can't use non-contiguous free space.  Try this...

Select /dev/sda6 and select Move.  Drag it all the way to the right so that the unallocated space is at the beginning of your extended partition.

Now select the extended partition, /dev/sda2, and resize it by dragging the arrow on the left side over to the right.  This should move your unallocated space outside of that extended partition and you should be able to grow your NTFS partition.

---

### Post by MaximoMilkman on 2009-03-25
When i try to unmount /dev/sda6 (I have to Unmount it to move it im assuming?) this error comes up

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

I have the linux Swapoff

---

### Post by MaximoMilkman on 2009-03-25
i also dont even know how to resize my extended partition they are always locked so i cant resize them?

---

### Post by logos34 on 2009-03-25
You might want to post a screenshot of gparted to give us a better idea what's going on

---

### Post by MaximoMilkman on 2009-03-25
I previously did but you didnt read it so i will repost it here...
[SIZE="5"][COLOR="Red"]
SCREENSHOT[/COLOR][/SIZE]

[[SIZE="5"][COLOR="Blue"]http://www.picamatic.com/view/3012994_Gparter/[/COLOR][/SIZE]]("http://www.picamatic.com/view/3012994_Gparter/")


Also if someone can establish a REMOTE DESKTOP connection with me and be able to move my mouse around and fix this problem that is OK with me.. Idk what program there is on linux that does this but i know teamviewer on windows works... i heard something like TightVnc does this... I dont know how to install programs from source though so i would need someone to tell me how to do it..

---

### Post by sgosnell on 2009-03-25
You can't make sda1 larger unless there is contiguous room for it.  You need to delete one of the swap partitions (the inside one), then move sda2 to the right, putting the unallocated space next to sda1, so that it can expand into the unallocated space.

---

### Post by logos34 on 2009-03-25
oops I missed the image link..

like sgosnell says, you need to move / (sda6) over to the right so the unallocated space is on the left, then shrink the extended partition sda2 to the right to free it up for windows.  BOTH swaps need to be turned off, otherwise it locks up your entended partition

---

### Post by MaximoMilkman on 2009-03-25
> **sgosnell said:**
> You can't make sda1 larger unless there is contiguous room for it.  You need to delete one of the swap partitions (the inside one), then move sda2 to the right, putting the unallocated space next to sda1, so that it can expand into the unallocated space.

When he said i need to delete one of the swaps by the inside one which one does he mean... And how do i "Move" Sda2 to the right?? Just click and drag or something like that?

---

### Post by sgosnell on 2009-03-25
Click on the swap partition and select delete.  Then Apply.  Then you can click on sda2, and drag the right edge to the right, all the way to the remaining swap partition.  You do not need two swap partitions. Then drag the left edge to the right, to whatever size you want, and click Apply.  Then drag the right edge of sda1 to the right to meet the left edge of sda2, and apply again.

---

### Post by MaximoMilkman on 2009-03-25
i Cant move these partitions to the right.. First off i dont know how to move them.. 2nd off I CAN NOT unlock the extended partition or ext3 I have deleted one of my LINUX SWAPS and when i try to unmount the ext3 it says i cant because something else is mounted on it.. im guessing the extended thing? Please help.. How do i "Move partitions" do i right click them do i use the edit menu or something here is my error...



[COLOR="Red"][SIZE="4"]Could not unmount /dev/sda6

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.
[/SIZE][/COLOR]

---

### Post by sgosnell on 2009-03-25
You are booting from a live CD or something similar, not from the drive(s) you're trying to change, aren't you?  Changing the partitions when they're in use won't work.

---

