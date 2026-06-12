---
title: "NTFS partitions not recognized by Windows.."
date: 2009-01-20
forum: General Help
---

### Post by Tuliku on 2009-01-20
Hi..

Living in Prague, resulted in buying a new laptop with Czech windows on it.
Since i am Dutch, and don't know the Czech language very well, i erased windows, and installed Ubuntu 8.10.
Created a few partitions using Gparted, keeping in mind that i will also want to install a English version of windows for the girlfriend who uses the laptop also every now and then.

Partitions look like following:

== 320 GB toshiba hard drive ==
sda1 - 050 GB NTFS
sda2 - 002 GB Swap
sda3 - 060 GB ext3 - /home
sda4 - extended
- sda5 - 008 GB ext3 - /
- sda6 - 200 GB NTFS

Ubuntu works fine, me happy.
But now trying to install Windows XP Pro on the first partition, but it fails.
During the startup of the installation of Windows, it does not see my hard drive...

is this because it is marked by linux as "sda1" / "sda6" ?
Or is there some other reason....?

BTW, laptop specs are Toshiba NB100, 2 GB memory, 320 GB harddisk, Intel Atom 270

Thanks in advance for any advice / solution.
Tuliku

---

### Post by taurus on 2009-01-20
You can use gparted in System -> Administration (install it if you don't have it on your machine) and format /dev/sda1 to fat32/vfat.  Hopefully, windows will pick it up then.

Otherwise, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

And by the way, if you install windows, it will overwrite GRUB from MBR so you won't be able to boot Ubuntu anymore.  Therefore, you need to reinstall GRUB to MBR again if you want to boot both OSes.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2009-01-20
I've seen a few cases where Windows refused to install to a drive because it turned out the drive's partition table was slightly corrupt. I think it would be worth at least making sure that's not your problem, so if that sounds OK with you, please post:
```
sudo sfdisk -luS
sudo sfdisk -d
```
Also, does the Windows Install CD you have come with SP1? If not, that might be the issue, because without SP1 I think the Windows CD can't deal with a drive larger than 137 GB (I don't know if your drive is larger than that though). Another cause I've seen of Windows refusing to install is if you have AHCI enabled for the HDD in your BIOS, although I'm not sure if that will always cause the Windows CD to balk.

---

### Post by Tuliku on 2009-01-20
Before i had it actually partitioned as FAT32, but also no luck.
Therefore i searched on this forum on how to format the partition to NTFS, and found that the tool Gparted can do this. Installed it, formatted it to NTFS, and still the same result.

Here is the outcome of that command:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21787571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6088    48901828+   7  HPFS/NTFS
/dev/sda2            6089        6330     1943865   82  Linux swap / Solaris
/dev/sda3            6331       13625    58597087+  83  Linux
/dev/sda4           13626       38913   203125860    5  Extended
/dev/sda5           13626       14598     7815591   83  Linux
/dev/sda6           14599       38913   195310206    7  HPFS/NTFS

---

### Post by Tuliku on 2009-01-20
**Here the outcome of "sudo sfdisk -luS":**

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  97803719   97803657   7  HPFS/NTFS
/dev/sda2      97803720 101691449    3887730  82  Linux swap / Solaris
/dev/sda3     101691450 218885624  117194175  83  Linux
/dev/sda4     218885625 625137344  406251720   5  Extended
/dev/sda5     218885688 234516869   15631182  83  Linux
/dev/sda6     234516933 625137344  390620412   7  HPFS/NTFS


**Here the outcome of "sudo sfdisk -d":**

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 97803657, Id= 7, bootable
/dev/sda2 : start= 97803720, size=  3887730, Id=82
/dev/sda3 : start=101691450, size=117194175, Id=83
/dev/sda4 : start=218885625, size=406251720, Id= 5
/dev/sda5 : start=218885688, size= 15631182, Id=83
/dev/sda6 : start=234516933, size=390620412, Id= 7


Yes, the windows cd contains SP1 integrated.
Another yes, AHCI enabled in my bios.
Should i switch it off and try again ?

---

### Post by caljohnsmith on 2009-01-20
Your partition table looks OK to me, so I would go ahead and turn off AHCI for the HDD and see if that lets you install Windows. Let me know if that works or not.

---

### Post by theozzlives on 2009-01-20
I would let Windows create your NTFS partitions. Your drive letters will be funny, but it should work.

---

### Post by Tuliku on 2009-01-20
Turned the AHCI off, but during reboot i forgot to press enter to boot from the windows cd.
Linux failed to start, some long messages..
Reboot again, pressed enter to boot from cd, and now windows is installing fine :-)

Thanks for the advices, and i will check the link on fixing the after the installation.

But one worry though, after installing windows, it looks like Ubuntu will not work when AHCI is turned off. Anyone happen to know if windows will work once it is installed with AHCI turned on ?

---

### Post by Tuliku on 2009-01-20
> **theozzlives said:**
> I would let Windows create your NTFS partitions. Your drive letters will be funny, but it should work.

That was sadly enough not possible as the windows installed didn;t see the whole disk at all.

But with AHCI turned off, all is working fine for the installation...

---

### Post by caljohnsmith on 2009-01-20
> **Tuliku said:**
> 
But one worry though, after installing windows, it looks like Ubuntu will not work when AHCI is turned off. Anyone happen to know if windows will work once it is installed with AHCI turned on ?
Glad to hear Windows is installing, but unfortunately having AHCI off will cause problems with Ubuntu as you've all ready experienced. I'm not sure if reinstalling Ubuntu would help, or if there is some kernel parameter you could pass to Ubuntu at boot time in order to make it work. I remember someone else in the forums with the same problem, and I think they ended up just having to switch AHCI on/off depending on which OS they wanted to boot. I would think there is a better way, so I wouldn't give up hope. What were the errors you got when booting Ubuntu?

---

### Post by Tuliku on 2009-01-20
Not sure, it was something with "initram>" or something like that.

Sadly enough windows failed after 3 tries.
Once it had copied all the files to the disk, and it rebooted to start from the disk, it lost contact with the usb cd drive, and could not continue with copying files from some "asms" folder.
Changed the AHCI on again, and hell broke loose. Blue screen etc.
Tried it 2 more times, same result.

Now using the live ubuntu cd to fix the MBR and use ubuntu again.
Will do some more research if windows is possible.
If not, then my girlfriend has bad luck and only Ubuntu on my laptop.

---

### Post by Tuliku on 2009-01-20
Damn... i think the bluescreens killed the partitions or something.. 
By following [these instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), i can not find the grub part, nor any partition on my hard disk...

Tonight at home i will try a full installation again.
Will keep you posted..

---

### Post by caljohnsmith on 2009-01-20
I think you might be in luck, because since you posted the output of sfdisk -luS and sfdisk -d, we have a perfect online backup of your original partition table. If all Windows did was erase the partition table, we can fix that, but the question is whether Windows actually overwrote the Ubuntu partition. How about posting the full output of:
```
sudo fdisk -lu
```
And we can go from there if you want.

---

### Post by Tuliku on 2009-01-21
Hi, thanks for that but since it would be an issue to run dual boot with ubuntu and windows (i don't want to change my bios settings with every startup), i decided to reinstall the whole disk with only ubuntu.

During the installation it showed that all the partitions are still ok, except the NTFS one.

Erased all, and did a fresh install.
Now it looks like

sda1 - 500 mb - /boot
sda2 - 10 gb - /
sda3 - 2 gb - swap
sda4 - the rest of the disk - /home

I'm happy with this, my girlfriend a bit less, but maybe this will help her a bit to be open for linux :-)

Bye for now, and thanks for all the help.

---

### Post by Liakath on 2009-01-22
Dear Tulliku

**[COLOR="Red"]Sorry for hijacking this thread. But I am also in a similar situation and trying to find a solution.Hope you will not mind[/COLOR]**

I am using a Desktop whose details are in my signature with WinXP & Ubuntu 8.10 in dual boot.

I had a my motherboard intel 915 GAV failure and since it is not available readily had to go in for a new motherboard "**GIGABYTE S series Motherboard model GA-G31M-S2L**" which supports the Intel Core 2 Multi-Core Processors.

After this change I was able to boot using GRUB menu to my Ubuntu installation and able to access all the NTFS partitions without any problems.

But trying to boot into Windows XP SP3 gives me boot disk failure message. So I had decided to repair the Windows XP installation but unable to do so as the Windows boot disk goes in to no action mode after the initial message [B]"Checking the Hardware Configuration....."
[/B] but fails to go forward.

```
sudo fdisk -l gives Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b580b57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306       14593   106735860    f  W95 Ext'd (LBA)
/dev/sda5            1306        4569    26218048+   7  HPFS/NTFS
/dev/sda6            4570        7833    26218048+   7  HPFS/NTFS
/dev/sda7            7834       11097    26218048+   7  HPFS/NTFS
/dev/sda8           11098       11221      995998+  82  Linux swap / Solaris
/dev/sda9           11222       11239      144553+  83  Linux
/dev/sda10          11240       13137    15245653+  83  Linux
/dev/sda11          13138       14593    11695288+  83  Linux

```

```
liakath@liakath-desktop:~$ sudo sfdisk -luS

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  20964824   20964762   7  HPFS/NTFS
		end: (c,h,s) expected (1023,254,63) found (280,254,63)
/dev/sda2      20964825 234436544  213471720   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5      20964888  73400984   52436097   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      73401048 125837144   52436097   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7     125837208 178273304   52436097   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8     178273368 180265364    1991997  82  Linux swap / Solaris
/dev/sda9     180265428 180554534     289107  83  Linux
/dev/sda10    180554598 211045904   30491307  83  Linux
/dev/sda11    211045968 234436544   23390577  83  Linux

```

```
liakath@liakath-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id= 7, bootable
/dev/sda2 : start= 20964825, size=213471720, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 20964888, size= 52436097, Id= 7
/dev/sda6 : start= 73401048, size= 52436097, Id= 7
/dev/sda7 : start=125837208, size= 52436097, Id= 7
/dev/sda8 : start=178273368, size=  1991997, Id=82
/dev/sda9 : start=180265428, size=   289107, Id=83
/dev/sda10: start=180554598, size= 30491307, Id=83
/dev/sda11: start=211045968, size= 23390577, Id=83

```

Apparently there seems to be a corruption in the partition table entries. Windows boot disk is unable to recognize sda1 partition may be because of problem in the Partition Table. How to go about rectifying the situation. 

I need my Win XP occasionally for my Games.

Please help

---

### Post by caljohnsmith on 2009-01-22
**Liakath**, I looked over your partition table, and it actually looks fine from everything I can tell. In my experience, you don't need to worry about the CHS (Cylinder, Heads, Sectors) geometry errors that sfdisk/fdisk might give, because usually all that means is that you just used a Windows partition program on the drive at some point; the idea of the CHS geometry is irrelevant for today's large HDDs, so the partition software can assume just about any arbitrary CHS geometry it wants to when it sets up your partition table. All linux partition programs that I'm aware of assume a 255 heads and 63 sectors/track geometry, but I've seen some Windows partition programs use 240 heads or 15 heads for their geometry assumptions. The bottom line is it doesn't matter; all modern OSes have to use LBA (Logical Block Addressing) to access the drive rather than CHS, because CHS is limited to a maximum drive size of only 8.4 GB if I remember correctly. 

So I think the problem with your Windows CD probably has more to do with your new motherboard, rather than a corrupt partition table. Is the Windows HDD IDE or SATA? Another thing that can cause the Windows CD to balk is if you have "AHCI" enabled for the drive in your BIOS. If you do have AHCI enable, try disabling it. Let me know how that goes.

---

### Post by Liakath on 2009-01-22
Dear coljohnsmith,

> **caljohnsmith said:**
> **Liakath**, I looked over your partition table, and it actually looks fine from everything I can tell. In my experience, you don't need to worry about the CHS (Cylinder, Heads, Sectors) geometry errors that sfdisk/fdisk might give, because usually all that means is that you just used a Windows partition program on the drive at some point; the idea of the CHS geometry is irrelevant for today's large HDDs, so the partition software can assume just about any arbitrary CHS geometry it wants to when it sets up your partition table. All linux partition programs that I'm aware of assume a 255 heads and 63 sectors/track geometry, but I've seen some Windows partition programs use 240 heads or 15 heads for their geometry assumptions. The bottom line is it doesn't matter; all modern OSes have to use LBA (Logical Block Addressing) to access the drive rather than CHS, because CHS is limited to a maximum drive size of only 8.4 GB if I remember correctly. 

So I think the problem with your Windows CD probably has more to do with your new motherboard, rather than a corrupt partition table. Is the Windows HDD IDE or SATA? Another thing that can cause the Windows CD to balk is if you have "AHCI" enabled for the drive in your BIOS. If you do have AHCI enable, try disabling it. Let me know how that goes.

I have only one HDD which is a Seagate 120 GB SATA drive. I have not tinkered with the BIOS settings as far as I remember and earlier it was working fine. May be the new motherboard created some incompatibility.

However will appreciate if some light is thrown on Enabling / Disabling "AHCI". The change I have seen is previouly it was having S.M.A.R.T enabled and now it shows it Disabled and the HDD is connected to IDE1 Channel as primary and CD/DVD Drive is in IDE0 Channel secondary. Are these settings fine? Have they to be different as the disk is SATA?

I will need a walk through how to set it up in case these are creating any problem.

Thanks for your time and effort.

---

### Post by caljohnsmith on 2009-01-23
If your HDD is SATA, I believe you need special SATA drivers to install Windows to it. When you boot the Windows CD, at some point near the beginning you can press "F6", and then Windows will let you load the SATA drivers from a floppy. Or if you don't have a floppy, you can "slipstream" the SATA drivers into the install CD:

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)

But the best solution might be if your BIOS offers "IDE-emulation" or "IDE-compatibility" mode for your SATA drive, because then you can make the SATA drive look like an IDE drive and the Windows CD should be happy. Hopefully one of those options will work for you, and let me know how it goes.

---

### Post by Liakath on 2009-01-23
Dear caljohnsmith,

> **caljohnsmith said:**
> If your HDD is SATA, I believe you need special SATA drivers to install Windows to it. When you boot the Windows CD, at some point near the beginning you can press "F6", and then Windows will let you load the SATA drivers from a floppy. Or if you don't have a floppy, you can "slipstream" the SATA drivers into the install CD:

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)

But the best solution might be if your BIOS offers "IDE-emulation" or "IDE-compatibility" mode for your SATA drive, because then you can make the SATA drive look like an IDE drive and the Windows CD should be happy. Hopefully one of those options will work for you, and let me know how it goes.

I do not come to the stage where in I can provide the required drivers for SATA; the CD starts up and after the initial message of "Inspecting the Hardware configuration....." it just hangs. May be it just does not find the C: partition to its liking. Trying to set it up as FAT32 / NTFS through GParted also does not help.

I will try out your other solution. Not missing much as Ubuntu is happy with the drive and most of my documents / pictures / mp3s / videos are still available to me through it. 

Only an occasional game I miss which is not much.

But trying to set it up as IDE in BIOS was also not much help. Still the situation remains the same.

Thanks for the time and efforts.

Liakath

---

### Post by Liakath on 2009-01-27
**[COLOR="Red"]**** UPDATE ****[/COLOR]**
I was able to resolve the problem and was able to install Windows XP by following the steps enumerated below:

**[COLOR="Red"]I am assuming your GRUB is intact and you are able to get in to Ubuntu without any problem (As it was in my case)[/COLOR]**

1. Format the sda1 partition as FAT32 using GParted.

2. Reboot using an Old Windows 98 Disk or MSDOS boot floppy (If you happen to have it) to command prompt.
Reformat C: partition and make it a system disk using the command FORMAT C: /s (which copies COMMAND.COM, MSDOS.SYS and few other system files). It may not recognise you disk fully or the other partitions in it - no worry.

3. Reboot in to Ubuntu and then copy the Windows XP disk contents as a separate folder in this partition including hidden files if any (Say WinXP Folder)- This copying I was unable to do under DOS due to many sub folders in Windows XP disk

4. Reboot through GRUB to this partition getting a C:> prompt.

5. Install Windows XP from the hard disk using WINNT.EXE which is available in the I386 folder by running the follwing command
**C:\WinXP\I386\WINNT**.

This is a DOS based install which takes a bit of time but ultimately copies the needed installation files to hard disk partition C: and then proceeds to the usual GUI based install which completes the installation.

(During this it may ask you for SMART Disk drivers; you may ignore and subsequently add the drivers later. Also it converts the drive to NTFS with your permission)

Once Windows XP is on you may add the Mother Board drivers etc.

6. Of course this process overwrites the GRUB which you have to reinstall.

**Hope this method works for others also who are in a similar situation.**

Liakath

---

### Post by Tuliku on 2009-03-01
I just found out where the issue was with my unsuccessful try before.
The windows xp disk i used was with SP1, and apparently it does not recognise sata. Now tried it again with a windows xp sp3 disk, and all works fine..

---

### Post by Tuliku on 2009-03-09
These days I'm running a triple boot on my nb100. (win xp sp3, ubuntu 8.10, mac osx 10.5.4)
I know that some people don't like the fact of Mac OSX being described here, so if someone wants more details, send a message to me.

---

### Post by jimoz on 2009-03-23
Sorry to hijack this thread... again

I'm in a similar situation. I run Ibex on a dual boot system with vista. The hard drive was a little disjointed so I tidied it up by removing a couple of partitions using GParted, which moved the Vista NTFS partition to the left to the start of the disk (It was previously the second partition).
Unfortunately now it doesn't run at all.
When tried to boot through grub, it doesn't output anything, just a cursor (I've triple checked my grub entries and am sure this isn't a problem).
I tried to boot vista through virtualbox, which output an error something like "Fatal error: cannot read from the selected medium".
Initially GParted would identify the NTFS partition OK, but through fdisk would identify it as FAT16. So I downloaded Fix-It Pro, burnt the rescue disk, and used it to fix the vista partition.
NOW... nothing recognises the NTFS partition. All the data should still be intact though... right?
Most of my documents were already backed up onto an external drive, so that isn't too much of an issue. I don't have any means to reinstall vista though, and as much as i hate it, i still use it occasionally for some software.
Any ideas?


The current situation:

> sudo sfdisk -luS
Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2   *        63 104181524  104181462   6  FAT16
/dev/sda3     104181525 230436359  126254835  83  Linux
/dev/sda4     230436360 234436544    4000185  82  Linux swap / Solaris

> sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=104181462, Id= 6, bootable
/dev/sda3 : start=104181525, size=126254835, Id=83
/dev/sda4 : start=230436360, size=  4000185, Id=82

---

