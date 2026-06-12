---
title: "Windows wont boot"
date: 2009-06-17
forum: General Help
---

### Post by mitchewr on 2009-06-17
Ok so i installed ubuntu 9.04 a while ago.  well ever since then windows wont boot up.  the computer sees that there is a partition for windows but it doesn't recognize that windows is on it. . . it simply recognizes another partion space that is not part of ubuntu.  So my question is that, now that ive installed gparted, is there a way to redo (or something) the partions so that windows will boot, or will i just have to start over from scratch and reinstall windows and ubuntu?  

Also when I first installed ubuntu, I think i did something wrong.  What i did was i just tested it from the cd to make sure it worked and stuff and then i clicked the install button.  Was i suppose to create a partion for ubuntu first and then start the installation?  Im guess im not sure cause i just watched  a video of someone installing ubuntu dual booting with windows and they created a partion for ubuntu before they actually started the installation process.  

I am (well was) running windows xp 32 bit version.  

Also, when you edit the partitions, are u suppose to mount the windows partition at all?  cause when i first installed ubuntu, i mounted the windows partition (i guess to ubuntu) and then the computer didn't recognize that there was even a separate partition in the computer.  Then when I installed ubuntu the second time, I didn't mount the windows partion and now the computer sees the separate partition, but it like doesn't see windows on it let alone boot windows up.  

I could use a little help here, haha.

---

### Post by ptn107 on 2009-06-17
Pop open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo fdisk -l
```
Paste the output here.

---

### Post by mitchewr on 2009-06-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9aba9ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1491    11976426    b  W95 FAT32
/dev/sda2            1492        9697    65914695    5  Extended
/dev/sda4            9698        9729      257040   88  Linux plaintext
/dev/sda5            1492        4169    21511003+  83  Linux
/dev/sda6            4170        9697    44403628+  82  Linux swap / Solaris

---

### Post by lindsay7 on 2009-06-17
Do you have your windows xp install disk with you? \

Looks like you have just one hard drive, is that correct?

---

### Post by mitchewr on 2009-06-17
yes to both

---

### Post by lindsay7 on 2009-06-17
Well, this does not look good. There is no windows partition on your drive at this time.

---

### Post by mitchewr on 2009-06-17
are u serious!?  how did that happen?  Well more like what did I do?  lol

---

### Post by lindsay7 on 2009-06-17
Her is the info on what to do. Note there are other setups listed here too.

Sorry this happened to you.  I will follow your post and help if I can.


[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by lindsay7 on 2009-06-17
You could also download "testdisk" and see if you can recover the windows partition.

---

### Post by mitchewr on 2009-06-17
huh. . . well alright cool.  Thanks

Just curious. . . what is on the partition that used to be windows then?  cause like it was all windows and then i shrunk it down to make room for ubuntu and now it's like windows is totally gone.

---

### Post by lindsay7 on 2009-06-17
> **mitchewr said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9aba9ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1491    11976426    b  W95 FAT32
/dev/sda2            1492        9697    65914695    5  Extended
/dev/sda4            9698        9729      257040   88  Linux plaintext
/dev/sda5            1492        4169    21511003+  83  Linux
/dev/sda6            4170        9697    44403628+  82  Linux swap / Solaris


As you can see Windows is not listed at all and there is no NTSF or windows partitions.  There is a small fat32 partition and there is a partition  called Linux plaintext (I have not seen this before, so I do not know what it is). Other than the fat32 partition the rest of the disk is an extended Linux partiton.

Like I said, you could get "Testdisk" and see if you could recover the windows partition. If it did, I am not sure your Ubuntu installation would still be intact.

---

### Post by swerdna on 2009-06-17
Whoa -- don't go deleting your windows partition. It's maybe sda1.

This line:> /dev/sda1 * 1 1491 11976426 b W95 FAT32says that a windows compatible partition of about 12 GB resides in the first partition of the drive. That looks classical windows partition. The asterisk says it's a bootable partition, just like windows. Mount it and see if the windows files are in there.

Create a spot to mount it with this terminal command:```
sudo mkdir /mnt/fat32
```Then mount it with this command:```
sudo mount -t vfat -o utf8=true /dev/sda1 /mnt/fat32 
```That will give read-only access to confirm that it's the windows partition.

Cruise to /mnt/fat32 in Nautilus and have a look inside.

reference for vfat: [http://www.swerdna.net.au/linhowtofat32.html](http://www.swerdna.net.au/linhowtofat32.html)

---

### Post by mitchewr on 2009-06-17
well. . . *SIGH* i went to reinstall windows from scratch following the link that was posted on page one. . . well i backed everything up first and then put in my recovery disk. . . and then one thing led to another and all my partitions got erased somehow. . . so long story short, i am on internet explorer in windows and am now getting ready to re-install ubuntu. . . sure wish i had waited a little bit longer to try and do the whole recovery thing but u can't cry over spilled milk so. . . i am now off to reinstall ubuntu. 
 
Any tips for me this time around so that when i'm all done i will still have windows, and it will be able to boot?
 
P.S. 
 
-I hate windows. . . it's so fricken complicated and never works the way u want it to. . . . argh!!

---

### Post by raymondh on 2009-06-17
> **mitchewr said:**
> Any tips for me this time around so that when i'm all done i will still have windows, and it will be able to boot?



For references ....

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Good luck.

---

### Post by mitchewr on 2009-06-17
haha thanks, I'll need it

---

### Post by swerdna on 2009-06-17
Tip would be to install windows to a limited size, maybe 10-15 Gb and then let the Ubuntu installer have the rest.

Lessons: windows installs to fat32 for the older releases and some older notebooks. fat32 is a windows partition.

---

### Post by mitchewr on 2009-06-17
yea thats what i did, i just gave it 10 gigs and it worked . . . I can now dual boot windows and ubuntu.

Thanks to all of you for your help.  This is another reason why I like ubuntu better than windows.  If i have a problem with ubuntu i can come here or just google search my problem and i get plenty of anwers.  Whenever i had a problem in windows i'd be lucky if i found one thing that was even remotely related to helping me let alone actually solve my problem.  

Ubuntu is THE BEST!!    GO LINUX

---

