---
title: "Accessing EXT3 from Windows 7 RC"
date: 2009-06-02
forum: General Help
---

### Post by SnowPunk98 on 2009-06-02
I upgraded from Vista to the RC of Windows 7 the other night. I had been using ext2fsd with great success. After reinstalling it on Windows 7 when I browse my EXT3 volume I tend to get a BSOD. I am using the newest version and have read of problems with ext2ifs as well.

Anyone having any success?

---

### Post by farmer26 on 2009-06-10
Bump! I am in the same boat here, looking for a way to access my ext3 partition from Windows 7.

The new OS is looking pretty good so far, I actually quite like using it! ;)

---

### Post by SnowPunk98 on 2009-06-10
I emailed the author of ext2ifs and he said Windows 7 is not supported and he probably would not have something released before Windows 7 is officially released.

I have had mixed success with ext2fsd and liked it better in Vista anyways. However with ext2fsd I get frequent BAD_POOL_HEADER blue screens when accessing my EXT3 partition.

At this point I am considering backing up my data and changing my /home to FAT32.

---

### Post by michy99 on 2009-06-10
> **SnowPunk98 said:**
> At this point I am considering backing up my data and changing my /home to FAT32.

Bad idea, as FAT32 does not support linux permissions, and some configuration files in /home need certain permissions set.

A better idea would be a separate data partition for files you want to access from Windows. I would consider making it NTSF instead of FAT32, though.

---

### Post by SnowPunk98 on 2009-06-10
Are there any disadvantes to using NTFS over EXT3 from a Linux perspective? I already have read/write access to my Windows NTFS volume.

---

### Post by michy99 on 2009-06-10
> **SnowPunk98 said:**
> Are there any disadvantes to using NTFS over EXT3 from a Linux perspective? I already have read/write access to my Windows NTFS volume.

From Linux perspective ext3 is better. I was only suggesting NTFS for a partition to be shared with Windows.

---

### Post by dardf on 2009-06-15
I am able to access my Ext3 partition in Windows 7 x64 using ext2fsd. The issue here is, Windows 7, by default does not allow any non WHQL drivers to be run. In order to run non-signed (which is the case for all ext2/3 readers/writers currently) you have to enable test mode and then use the driver. 

1. An easy way to go about doing this is to download NGO's Driver Signature Enforcement Overrider (DESO): [http://www.ngohq.com/home.php?page=dseo](http://www.ngohq.com/home.php?page=dseo)
2. Enable test mode
3. Reboot
4. Install ext2/3 driver programs.
5. Mount your drives.

Edit: I should note that I only enabled Read-Only option in Ext2fsd, and reading from the drives has worked like a charm. I rather not experiment (with the potential loss/corruption of my data) with the write-to ext2/3 options. For those who are more brave, please post back with results.

---

### Post by SnowPunk98 on 2009-06-16
Were you able to install and run ext2fsd before using the DESO? 

I am able to use it most of the time without DESO, but sometimes I get a BSOD when I access the partitions.

---

### Post by dardf on 2009-06-18
Technically I was able to install the program (using build 7100 x64) without enabling test-mode, but the driver would not start. As in, you click on your newly mounted ext3 drive and it prompts you to format the drive so that you can use it.
I have yet to run into a bsod yet while accessing my partition. 

But I do find it interesting that you can use the driver without test-mode.. Do you by chance bsod when you try to write to an ext partition?

---

### Post by strange1712 on 2009-07-23
> **dardf said:**
> I am able to access my Ext3 partition in Windows 7 x64 using ext2fsd. The issue here is, Windows 7, by default does not allow any non WHQL drivers to be run. In order to run non-signed (which is the case for all ext2/3 readers/writers currently) you have to enable test mode and then use the driver. 

1. An easy way to go about doing this is to download NGO's Driver Signature Enforcement Overrider (DESO): [http://www.ngohq.com/home.php?page=dseo](http://www.ngohq.com/home.php?page=dseo)
2. Enable test mode
3. Reboot
4. Install ext2/3 driver programs.
5. Mount your drives.

Edit: I should note that I only enabled Read-Only option in Ext2fsd, and reading from the drives has worked like a charm. I rather not experiment (with the potential loss/corruption of my data) with the write-to ext2/3 options. For those who are more brave, please post back with results.

This is really usefull, tried the same combination and works flawlessly... Thank you very much!

---

### Post by SnowPunk98 on 2009-07-23
I have gotten the format drive thing before but that is normally not my problem. I can access the partition and normally I get the BSOD while browsing or opening a file, usually not when writing to it.

---

### Post by ceefour on 2009-10-31
If you want to dual boot Ubuntu with Windows 7 and read ext3 filesystem, you can use Ext2FSD. Although you may need to take special steps as explained below.

I’ve successfully used Ext2fsd on Windows 7 to read my ext4 (!) filesystem this way.

For those interested, more detailed how-to is here: [Read ext3/ext4 Partition from Windows 7]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/")

Hope this helps!

---

### Post by rmockler on 2009-10-31
The link referenced above in post #12 should do the trick. I have been using Ext2Fsd-0.48 to access my Linux partition with great success and NO BSOD or need for DESO, using Windows 7 Build 7600.

---

### Post by lenn-art on 2009-11-03
#12 did not work for me. I have an 300gb Ext2 datapartition in use for several years. Sometimes i get a Bad Pool Header message (BSOD) in Win7.

---

### Post by deobfuscate on 2009-11-15
A bugfix version of Ext2Fsd was released that resolved the BAD_POOL_HEADER BSOD on Windows 7, more info on my blog post here [http://www.deobfuscate.net/?p=514](http://www.deobfuscate.net/?p=514)

---

### Post by ceefour on 2009-11-15
> **deobfuscate said:**
> A bugfix version of Ext2Fsd was released that resolved the BAD_POOL_HEADER BSOD on Windows 7, more info on my blog post here [http://www.deobfuscate.net/?p=514](http://www.deobfuscate.net/?p=514)

Thank you deobfuscate! Nice info :popcorn:

---

### Post by confused_user on 2009-11-17
i love you 

i was on the verge ofblowing this windows 7 pos away after getting bad pool header everytime i used the damn thing.

thanks for the link

---

### Post by confused_user on 2009-11-17
actually i hate you (just kidding)

now i cant boot all the way to a desktop, it blue screens wth “Stop 0x0000007F every time now.

Before i put that .sys in it was fine until i started reading and writing to ext3.

now i'm ******.

---

### Post by confused_user on 2009-11-17
ok i'm back to loving you, you have to use the sys file in the fre folder, the one in the chk folder is bad mmmkay

---

### Post by jaisayan on 2009-11-18
I've created a new boot entry in BCDedit with -nointegritycheck option turned ON to install unsigned driver. Works perfectly.

---

### Post by SnowPunk98 on 2010-02-08
> **confused_user said:**
> ok i'm back to loving you, you have to use the sys file in the fre folder, the one in the chk folder is bad mmmkay

:d

---

