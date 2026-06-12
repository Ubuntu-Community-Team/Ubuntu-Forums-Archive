---
title: "Dell Studio 15 Ubuntu not seeing Partitions"
date: 2011-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr_PS3 on 2011-02-05
Hello Linux Community. I have wanted to install Ubuntu on my Dell Studio 15 laptop for a month now and finally have the time to do it. My problem is when I try to install Ubuntu 10.04, the installer only shows my whole hard drive as "unallocated space." I do have Windows 7 on part of my hard drive that I wish to keep along side with Ubuntu. I tried partitioning the hard drive in Windows 7. It worked and says 80GB of unallocated space on my 320GB hard drive.

What is wrong? Why will my whole hard drive show as unallocated space on Ubuntu Live CD, but on Windows it shows the correct only 80GB partition.

My specs on a Windows 7 64-bit system:
Dell Studio 1558
320GB SATA Hard Drive
4GB DDR3 Ram
Intel i5 Processor M520 @ 2.40GHz
ATI Mobility Radeon HD 4500 Series

---

### Post by ajgreeny on 2011-02-05
Run the live CD/USB until you get to the desktop, then double click the Install ubuntu icon.  At the partitioning page choose manual partitioning, the third option, I think, and see what partition layout that shows.  I should show your current Win7 OS plus any Restore partitions and Boot partition that Win7 seems to always have, as well as the unallocated space you have made.

If any problems come back again with screenshots from the live CD, if possible; just hit Print Screen key to do that, and then copy the pic back here as an attachment.

---

### Post by Mr_PS3 on 2011-02-05
First of all thank you for helping me. Here is the picture. At the screen before it the screen said "there are no operating systems installed.
What is the problem?

---

### Post by ajgreeny on 2011-02-06
Win7 still working?

---

### Post by Mr_PS3 on 2011-02-06
Windows 7 is still working. I noticed that while I was in the Ubuntu 10.04 Live CD that under the "Places" tab, a "a 234GB Filesystem" and "System Reserved" were listed. I clicked on the 234GB Filesystem and sure enough it gave me access to my Windows 7 partition. The System Reserved was the boot loader.

---

### Post by ajgreeny on 2011-02-06
OK, so now from the live CD run ```
sudo fdisk -l
``` (lower case L at end) and report back output.  You could also while in live CD run **System >Administration >Gparted** and attach a screenshot back here.

---

### Post by Mr_PS3 on 2011-02-06
Here is the screen shot. I tried to show the "Places" tab, but wasn't able to.

---

### Post by ajgreeny on 2011-02-06
It looks like you have a GPT (GUID) partition table, but as that really means nothing to me other than it's not a standard msdos type, I will point you to [http://www.uluga.ubuntuforums.org/showthread.php?t=1619381](http://www.uluga.ubuntuforums.org/showthread.php?t=1619381) where there seems to be a lot of info.

Instead of fdisk, as the error tells you, try ```
sudo parted -l
```which should at least show you the partitions, and if parted does, I think gparted also should.

---

### Post by srs5694 on 2011-02-06
The problem is not that the disk *is* a GUID Partition Table (GPT) disk, but that it *used to be* a GPT disk and was incompletely converted back to Master Boot Record (MBR) form, leaving residual GPT data structures that are confusing libparted (upon which the Ubuntu installer's partitioner and several other tools are based).

I recommend you boot your Ubuntu installer into the "try before installing" mode (or whatever it's called), download [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) (you'll need the .deb file for your architecture -- i386 or amd64), install that packabe by double-clicking or typing "sudo dpkg -i gdisk_*deb" in a shell prompt, and then read [this page](http://www.rodsbooks.com/gdisk/wipegpt.html) from the GPT fdisk documentation to learn how to wipe the old GPT data. Note: *Do not* use the version of gdisk in the Ubuntu repositories unless you're installing the 11.04 alpha; the version in the repositories for earlier versions of Ubuntu is hopelessly out of date. IIRC, it's got bugs that will make matters worse if you try to fix the problem with it.

---

### Post by Mr_PS3 on 2011-02-06
> **srs5694 said:**
> The problem is not that the disk *is* a GUID Partition Table (GPT) disk, but that it *used to be* a GPT disk and was incompletely converted back to Master Boot Record (MBR) form, leaving residual GPT data structures that are confusing libparted (upon which the Ubuntu installer's partitioner and several other tools are based).

I recommend you boot your Ubuntu installer into the "try before installing" mode (or whatever it's called), download [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) (you'll need the .deb file for your architecture -- i386 or amd64), install that packabe by double-clicking or typing "sudo dpkg -i gdisk_*deb" in a shell prompt, and then read [this page](http://www.rodsbooks.com/gdisk/wipegpt.html) from the GPT fdisk documentation to learn how to wipe the old GPT data. Note: *Do not* use the version of gdisk in the Ubuntu repositories unless you're installing the 11.04 alpha; the version in the repositories for earlier versions of Ubuntu is hopelessly out of date. IIRC, it's got bugs that will make matters worse if you try to fix the problem with it.

Thank you so much both of you. So with GPT fdisk, what will it do to my hard drive? Will it change it to a Master Boot Record so Ubuntu will funciton normally on my computer? Will I still be able to use the Grub 2 bootloader with Windows 7 and Ubuntu 10.10 when I upgrade?

The whole GUID makes sense now. About a month ago I tried to do a hackintosh and couldn't get it. I decided to just reinstall Windows, so did I forget to format my hard drive back to an MBR?

Also, I noticed that I wasn't able to access my Windows 7 files. When Ubuntu installs, will I be able to?

Finally, if I get Ubuntu installed, will I ever have any more problems with the GUID partition table or installing any other files?

---

### Post by srs5694 on 2011-02-07
> **Mr_PS3 said:**
> Thank you so much both of you. So with GPT fdisk, what will it do to my hard drive? Will it change it to a Master Boot Record so Ubuntu will funciton normally on my computer? Will I still be able to use the Grub 2 bootloader with Windows 7 and Ubuntu 10.10 when I upgrade?

Technically, your disk is currently an MBR disk. Some background: GPT data structures include a "protective MBR," which is a valid MBR that contains a single partition of type 0xEE that's intended to protect the disk from meddling by GPT-unaware tools; primary GPT data structures; and backup GPT data structures. This means that the GPT data necessarily occupy more sectors than do the primary MBR data structures. (Logical partitions also occupy additional sectors, but they aren't likely to be the same sectors as the GPT data structures.) When converting from GPT to MBR with a GPT-unaware utility, there will therefore be a lot of GPT data left over.

The GPT specification clearly states that if the MBR contains no protective GPT entry (one with a type code of 0xEE), that it's not a GPT disk. Your disk has no type-0xEE MBR partition, so it's technically an MBR disk, not a GPT disk. Furthermore, since you can boot Windows, Windows is clearly using the disk as an MBR disk, so that's what it is from a functional point of view. At best, the GPT data duplicate your existing MBR partitions. At worst (and this is more likely), they provide contradictory partition information that, if some tool were to try to use it, could end up damaging your real partitions.

Your immediate problem is that libparted is getting confused by the valid MBR and leftover GPT data. You've got to clean out the leftover data.

> The whole GUID makes sense now. About a month ago I tried to do a hackintosh and couldn't get it. I decided to just reinstall Windows, so did I forget to format my hard drive back to an MBR?

It's currently in MBR format. The problem is that whatever utility you used (probably the Windows installer) did an incomplete job in converting it back, in that it didn't wipe all the GPT data.

> Also, I noticed that I wasn't able to access my Windows 7 files. When Ubuntu installs, will I be able to?

It's unclear what was unable to access your Windows 7 files. Was this the Ubuntu installer in "live CD" mode? Something else? In a normal Linux installation, it is possible to access Windows files. I suspect you either didn't know how to do this or there was a problem related to the leftover GPT data. In any event, I recommend you put this question off until after you've installed Linux, with one caveat....

It's unwise to regularly access any OS boot partition from another OS. In this specific case, Linux doesn't understand the security features that Windows uses on its filesystem, so it's easy to accidentally trash your Windows setup as an ordinary user in Linux. Also, although Linux's NTFS driver seems pretty reliable based on anecdotal reports, I find it hard to believe that it's as reliable as Windows' own NTFS support.

Thus, I recommend that when you repartition, you create a separate FAT or NTFS partition for shared data -- any files you might want to access in both OSs (MP3s, photos, etc.) or files you might want to transfer between OSs (if you download a Windows file in Linux, say). Mount and use this partition in both OSs, but when you're in Linux, *do not* mount the Windows C: partition. That'll keep the OS installation itself safe from damage.

> Finally, if I get Ubuntu installed, will I ever have any more problems with the GUID partition table or installing any other files?

If you wipe the GPT data, they will trouble you no more, unless you mess around with tools to convert the disk back to GPT form. I'm not sure what you mean by "installing any other files."

---

### Post by Mr_PS3 on 2011-02-10
After reading up on the GPT stuff I was finally able to install Ubuntu 10.04 and upgraded to 10.10. Thank you Ubuntu formus!

---

### Post by kentos93 on 2011-12-12
This is some problem.

---

