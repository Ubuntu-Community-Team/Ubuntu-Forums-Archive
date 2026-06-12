---
title: "Lost Data Recovery"
date: 2009-02-12
forum: General Help
---

### Post by maxideci on 2009-02-12
Hi, 

I have recently installed Intrepid Ibex on my Fujitsu Siemens Laptop. Now I have dual boot option, XP n Ubuntu 8.10 2.6.26.11.

Current Status:
My Laptop has a 80GB HD with 35 GB under XP, 4 GB of Linux Swap partition and rest Linux ext/3 partition.

Earlier Status, before installing Ubuntu 8.10 :
80 GB of which 45 GB was Windows partition and rest was ubuntu 7.04.
the windows partition was divided as (C: 15 GB, D:10 GB, E:10 GB all NTFS and F:10GB FAT32).

I wanted more HD space under Linux, so I decided to free some space and dedicate it to Linux. Thus, I deleted F:(FAT32) partition and installed Ubuntu 8.10 with almost 45 GB of raw space.

Now, I am quite happy about the whole setup and  on my way to say good bye to windows forever.

Yesterday evening, I realized, I have deleted and important picture folder(270 MB) from the earlier drive F:. **Is this folder or the contents of this folder recoverable under Linux ??? If yes how???** 

Life cycle of data of Drive F:
1) Deletion (Shift Del)
2) Partition Deleted (with XP install CD) to turn it into raw space for Linux installation.
3) Ubuntu-8.10 installed with ext/3 file system.

There is almost 30 GB of space free on Linux partition not including the swap.

**Is this folder or the contents of this folder recoverable under Linux ??? If yes how??? Does Intrepid Ibex comes with any inbuilt tool to recover lost data??**

Thanks, 

MaxiDeci..

---

### Post by caljohnsmith on 2009-02-12
First of all, I would strongly suggest not booting into your Ubuntu install on that HDD any more to maximize your chances of file recovery. There is some chance you might be able to recover the "F" partition using testdisk, so how about booting your Live CD, download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and more importantly, if any of the partitions look like they might be the lost "F" partition. We can work from there if you want.

---

### Post by maxideci on 2009-02-12
> **caljohnsmith said:**
> First of all, I would strongly suggest not booting into your Ubuntu install on that HDD any more to maximize your chances of file recovery. There is some chance you might be able to recover the "F" partition using testdisk, so how about booting your Live CD, download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and more importantly, if any of the partitions look like they might be the lost "F" partition. We can work from there if you want.
Hi caljohnsmith, 

thanks for the reply, I will try it and post the resuls ASAP.

cheers!!

---

### Post by maxideci on 2009-02-12
Hi CalJohnSmith, 

I did run the Test Disk utility, I have attached screen shots along with this post for your reference (I have not attached the Scr Shots of D: and E: partition, I could only allowed to upload 5 files here)

I could get the directory listings of All partitions except (Linux swap partition)

I don't see any files related to F: Partiton.

Thanks,

---

### Post by caljohnsmith on 2009-02-12
Unfortunately it looks like your Ubuntu install overwrote your FAT32 "F" partition enough that testdisk can't recover the FAT32 partition. Probably your best bet is to use a program like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover whatever files it can find; you could run the photorec program just on your linux and swap partitions, or whichever partitions overwrote the FAT32 partition. You'll need another drive or enough space somewhere to save all the recovered files to, so that means maybe 45 GB of space or so. You can either download the latest photorec from the website in the link above, or you can install it in Ubuntu with:
```
sudo apt-get install testdisk
```
Because photorec is part of the testdisk package. Good luck and let me know how it goes.

---

### Post by maxideci on 2009-02-12
Hi, 

I ran the Test Disk utility with log file on, just to see if i find something new, I attach it with post. Though, I see there is nothing related to F: Partition.

What should be the next steps.

Thanks,

---

### Post by maxideci on 2009-02-12
> **caljohnsmith said:**
> Unfortunately it looks like your Ubuntu install overwrote your FAT32 "F" partition enough that testdisk can't recover the FAT32 partition. Probably your best bet is to use a program like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover whatever files it can find; you could run the photorec program just on your linux and swap partitions, or whichever partitions overwrote the FAT32 partition. You'll need another drive or enough space somewhere to save all the recovered files to, so that means maybe 45 GB of space or so. You can either download the latest photorec from the website in the link above, or you can install it in Ubuntu with:
```
sudo apt-get install testdisk
```
Because photorec is part of the testdisk package. Good luck and let me know how it goes.
So, may I boot from HDD now to install testdisk and use photorec ???
Yes, I do have enough space on my External HD to recover 45 GB of data.

---

### Post by caljohnsmith on 2009-02-12
> **maxideci said:**
> So, may I boot from HDD now to install testdisk and use photorec ???
Yes, I do have enough space on my External HD to recover 45 GB of data.
Since your current Ubuntu install overwrites to at least some degree the files you want to recover, I would not recommend booting into Ubuntu on your HDD and running photorec from there; I would use your Live CD again. You can mount your external HDD while you are using the Live CD and direct photorec to save its files to the external HDD.

---

### Post by maxideci on 2009-02-12
> **caljohnsmith said:**
> Since your current Ubuntu install overwrites to at least some degree the files you want to recover, I would not recommend booting into Ubuntu on your HDD and running photorec from there; I would use your Live CD again. You can mount your external HDD while you are using the Live CD and direct photorec to save its files to the external HDD.
Woooo Hooooo!!! u r the best CalJohnSmith.... I have recovered almost all my files till now...the recovery is still going on ... i was so excited...i thought to share it with u ....i have so far recovered 190 files out of possible 250 odd files...and it has scanned 25% of space....

Thanks for timely help...

Will update later...

Ciao,

---

### Post by maxideci on 2009-02-13
Hi, 

I have recovered all my picture files, this is amazing ...absolutely amazing ...

Thanks, for helping in such a wonderful way.

I'm lovin ubuntu more n more....

Cheers!!!

---

### Post by caljohnsmith on 2009-02-13
That's great news you recovered all your lost files, maxideci, and I think you are very fortunate to get all your files back considering the circumstances. Cheers and hope you don't have to do any more file recovery any time soon. :)

---

