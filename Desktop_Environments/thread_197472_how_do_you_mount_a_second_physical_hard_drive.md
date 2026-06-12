---
title: "how do you mount a second physical hard drive"
date: 2006-06-15
forum: Desktop Environments
---

### Post by darkside6966 on 2006-06-15
im using kubuntu 6.o6  the system sees the d drive but wont mount it.

I have all my data files from windows xxx on it along with my mp3 files so i dont want to get this wrong.............:confused: 

Thank you all for your help in advanse

---

### Post by Sutekh on 2006-06-15
You should have a read of this link the follow the steps outlined in it to help you access your Windows partition

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

Depending on the filesystem format, you may only be able to read and execute files on the partition (NTFS).  FAT filesystems are more friendly to Linux and you should be able to completely access it.

---

### Post by darkside6966 on 2006-06-15
thanks i will look at your link and yes it is a nfts file system.  
I was also wondering if i can convert drives back to fat 32?

---

### Post by Sutekh on 2006-06-15
Ok great, the link shoud have everything you need, but if you get stuck, just ask.

Unless you really need to I think you could save a lot of problems by leaving it formatted as NTFS.   

If for some reason you need a partition that both Windows and Linux can *write* to, then you could create a new FAT32 partition or even an ext3 partition, which is native to Linux, and can be accessed through Windows using the [ Ext2 Installable File System For Windows]("http://%5BURL=%22http://fs-driver.org/%22")

---

### Post by darkside6966 on 2006-06-15
thanks for all your help, i will be working on this tommorrow.  Short term it will fit my needs however long term i want to go back to fat32 as at this point i plan on leaving the windows platform asap.  

I got sick and tired of having to call Mr. Gates everytime i changed or swaped hardware between my two systems and im sure vista will be more intrusive to the users  of windows and nfts will be a constant reminder that bill is watching you.............

---

### Post by Psed on 2006-10-20
I have a similar question, to the above, but my hda1 is Ubuntu ext3. I installed a 2nd hard drive and it shows as hdb1 and is ext3 . Trouble is it shows as inaccessible, and I cannot mount it.
Can you provide me with help so I may mount my 2nd hard and be able to access it?

Thanks, Psed

---

