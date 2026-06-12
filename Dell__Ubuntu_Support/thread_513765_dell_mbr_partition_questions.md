---
title: "dell mbr partition questions"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by johnn1949 on 2007-07-30
E1505 2GHz dual core,2GB,ATI X1400 graphics, 80 GiG drive,XP Media Center.

disk partitions
47 MB FAT EISA PARTITION

67.50 GB NTFS PARTITION (media center edition)
2.O GB FAT32 MEDIA DIRECT LOGICAL PARTITION

4.98 GB FAT32 (restore?)
-----------------------------------------------
Disks I have:
Xp reinstallation disk
dell dignostics and drivers disk
Media Direct reinstallation disk

Gparted live cd
------------------------------------
I created Dell Mediadirect repair utility disk

Acronis True Image 10 installed with current complete operating system backup on external usb drive.(which I have not tried to use, say a prayer)
-----------------------------------


I want to end up with XP Media Center on one partition,or one with one logical,partition, so I can do an installation of of Ubuntu  on a 20 GB partition. I don't really need MediaDirect but I would like the volume controls on the front panel to work when running window if possible. 
-----------------------------------------
1. If I delete the eisa and restore partition will the MBR still be there so windows will boot up and dell direct still be there?

2. If I install ubuntu on a new partition and use the grub to dual boot, Will I then loose the Dell direct? if so is there any way to make the volume controls work?

3. Should I replace The Dell MBR(assuming the miadirect won't work) with the XP MBR before I try the dual boot install.Can I do that by just running the xp Media center disk and repair MBR.

I plan to make a true image complete system backup of the hard drive when I get XP on one partition. Hopefully then I could install a different version of Ubuntu later if I wanted.

I have a toshiba (that only had one partition) running a dual boot so I understand that, but all this special Dell stuff really has me confused.

Any advice would be appreciated.
Thanks,John

---

### Post by Rocket2DMn on 2007-07-31
I guess it's not really clear what you are asking.  The suggested method for setting up a dual boot with WinXP is to completely wipe the drive, the install windows.  After you install windows, you can boot from the Ubuntu LiveCD and install.
Since you know how you want your partitions, you can proceed like so for a fresh dual boot setup:
1) Boot from WinXP cd and run the setup.  Delete all existing partitions.  Create ~60GB partition and install Windows on it.  As a note, most people who want to make the switch to Ubuntu wish they left more space for Ubuntu rather than Windows because they spend much more time using Ubuintu.  It's up to you.
2) WinXP installation is now complete.  Boot from the Ubuntu LiveCD and install Ubuntu on the remaining 20GB partition (or however large you wanted it).  You will need to provide a SWAP partition (about 1.5 times your RAM size).  The GRUB bootloader will also be installed - this is preferred.
3) Run Ubuntu! On computer bootup the GRUB screen will give you the option of what Ubuntu kernel to run from, and the WinXP option should be at the bottom.
More can be found here about installing and dual booting: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

So,
MBR: Use what Ubuntu gives you
Dell Direct: This sounds like software to me, your volume controls should work fine in Windows as long as you have the drivers installed.  They may need some configuring in Ubuntu, but they will probably work.  Those of us who move our laptops between docking stations, headphones, and internal speakers can run into problems, but for most users, it's fine.
Don't worry about all this dell stuff.  I run Ubuntu 7.04 on my Dell 600m laptop.  There are thousands of others who also use Ubuntu on their dells without these worries.

---

### Post by johnn1949 on 2007-07-31
Thanks for your answer. 

 The reason I asked the first question is I'm just trying to avoid reinstalling all my prorgrams ,updates,documents,etc. I was hoping if I deleted the 2 dell partitions and the logical partition, I would end up with an xp partition that would still boot.  Then I thought I could resize it with Gparted and then install ubuntu. 
 
    The Mediadirect  a program to run media without booting windows but I think with out it the control bottons on the front of the computer (including volume,play,fast forward etc.) don't work.

The only difference in the mbr is the option to run the recovery partition which  would be deleted anyway.That is why I asked if I should repair the mbr before insalling ubuntu.

I don't need media direct and I guess I can get along without the panel volume controls.

---

### Post by Rocket2DMn on 2007-07-31
> **johnn1949 said:**
> Thanks for your answer. 

 The reason I asked the first question is I'm just trying to avoid reinstalling all my prorgrams ,updates,documents,etc. I was hoping if I deleted the 2 dell partitions and the logical partition, I would end up with an xp partition that would still boot.  Then I thought I could resize it with Gparted and then install ubuntu. 
It is usually best to reformat because with Windows, files get thrown all over the place and defragging doesn't normally help enough if the computer has been getting used for awhile.  A fresh install just prevents problems, so long as you have good backups.
> The Mediadirect  a program to run media without booting windows but I think with out it the control bottons on the front of the computer (including volume,play,fast forward etc.) don't work.
If this is acting like it's own little operating system, you could set aside some space for it and it would probably work alongside Ubuntu since Ubuntu should recognize the partition as bootable and place it as a GRUB option.  Your media keys should work as they did before as long as the drivers are installed.
> The only difference in the mbr is the option to run the recovery partition which  would be deleted anyway.That is why I asked if I should repair the mbr before insalling ubuntu.
You can run a repair session from the XP cd, or by using System Recovery in XP.  Having an Ubuntu partition should not affect other partitions unless you tell it to.

---

### Post by johnn1949 on 2007-07-31
Thanks Rocket,
Excellent answers to my questions.  

As to backups, True image has created and verified them,  I hope they are good.

You have me convinced a clean install is the way to go. Then I'll have the XP mbr from the start too. Since the Media direct gets installed in a logical inside the windows partition I might even try that too before I add ubuntu.  

Thanks again, Ubuntu Forums rock.

John

---

