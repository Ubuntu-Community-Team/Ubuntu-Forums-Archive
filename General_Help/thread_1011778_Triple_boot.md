---
title: "Triple boot"
date: 2008-12-15
forum: General Help
---

### Post by doyouhas on 2008-12-15
Here is the deal. I wanted to install Ubuntu, XP, and Vista all on the same machine. Simple...right? Not. So my first thought it, wipe the disk clean and then create two ntfs partitions that are each roughly one third the size of the disk, and once XP and Vista have been installed on them, install Ubuntu using remaining free space. So that is exactly what I did, using GParted I wiped the disk clean and made two new ntfs partitions each 35 gig (the whole disk is 110 so 35 is roughly one third) and then I installed Vista on the first partition and XP on the second. Everything was ok up until I did those steps. Then I installed Ubuntu on the free space and once the computer restarted, in the GRUB menu I only saw an option for Vista and not XP. No big deal I thought. Well when I tried to boot into Vista I get "boot mgr missing." So I look around and find a help site that has a simple solution to this. I pop in the Vista install DVD and choose the repair option and then choose the repair boot option or something like that. Restart, and now I can boot into Vista. Great. Ok now what about XP? So I start Ubuntu, open up grub.conf and add in an entry for XP. I just copy the entry for Vista but change, obviously, the name, and the "root" option to the corresponding partition. Vista was on (hd0,0) so I made the "root" option for XP (hd0,1). OK. Restart, and now in XP I get the same "bootmgr missing" screen. Now I look at another article that says to fix this error, go into XP install disk and run the repair tool, etc, and run the "fixboot" or "fixmgr." I just remember I ran fixboot first and then fixmgr and now I get the following message before I even get to the GRUB menu: "ntldr is missing" So now, basically, my machine is ****** and I am stuck.
Suggestions?
I'm really in a pickle here, any help is appreciated.

---

### Post by zwygart on 2008-12-15
You are trying to do some difficult thing (2 windows). 
For the grub manual, look at this [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
So how to repair your computer. Boot into a grub environnement. Howto do this? Boot in the liveCD and type at the terminal grub, you should fall at a grub terminal. Type ```
find /boot/grub/stage1
```. This returns a line (hdX,Y). Remember the numbers X,Y. and replace it at the commands here ```
root (hdX,Y)
setup (hdX)
```.
This reinstall grub at the MBR. Now you have to edit your menu.lst.
I think you don't have multiple drives so no need of map.
Try to add the line : hide *partition*
add your windows blocks to hide the others partition (other windows).
If you have troubles post back.

---

### Post by zwygart on 2008-12-15
You are trying to do some difficult thing (2 windows). 
For the grub manual, look at this [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
So how to repair your computer. Boot into a grub environnement. Howto do this? Boot in the liveCD and type at the terminal grub, you should fall at a grub terminal. Type ```
find /boot/grub/stage1
```. This returns a line (hdX,Y). Remember the numbers X,Y. and replace it at the commands here ```
root (hdX,Y)
setup (hdX)
```.
This reinstall grub at the MBR. Now you have to edit your menu.lst.
I think you don't have multiple drives so no need of map.
Try to add the line : hide *partition*
add your windows blocks to hide the others partition (other windows).
If you have troubles post back and post also the block of your windows boot in menu.lst
It should something with chainloader

---

### Post by logos34 on 2008-12-15
If the 'hide' method doesn't work, you might want to consider coming at it from the windows side.  Grub doesn't always work with triple boot, so you could try **EasyBCD** to boot all three OSs, and reinstall grub to the ubuntu root:

> [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Master boot record and boot manager

GNU/GRUB is the boot manager installed in Ubuntu by default. If you use the Alternate CD you can choose Lilo instead. GRUB and Lilo are both good Open Source boot managers so the main parts of the boot loaders are installed inside Ubuntu. This means Ubuntu is independant and avoids any need for writing to other operating systems. To accomplish this, the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk. The MBR code is changed to point to the boot loader in Ubuntu. You will be presented with a list of operating systems and you can choose one to boot. If you do nothing Ubuntu will boot after a ten second countdown. If you select Windows then GRUB or Lilo will chainload Windows for you at the Windows boot sector, which is the first sector of the Windows partition. That is the least intrusive way to install Ubuntu.

If you have a problem with changing the MBR code, you might prefer to just install the code for pointing to GRUB to the first sector of your Ubuntu partition instead. If you do that during the Ubuntu installation process, then Ubuntu won't boot until you configure some other boot manager to point to Ubuntu's boot sector. Windows Vista no longer utilizes boot.ini, ntdetect.com, and ntldr when booting. Instead, Vista stores all data for its new boot manager in a boot folder. Windows Vista ships with an command line utility called bcdedit.exe, which requires administrator credentials to use. You may want to read [http://go.microsoft.com/fwlink/?LinkId=112156](http://go.microsoft.com/fwlink/?LinkId=112156) about it.

    * Using a command line utility always has its learning curve, so a more productive and better job can be done with a free utility called EasyBCD, developed and mastered in during the times of Vista Beta already. 

EasyBCD is user friendly and many Vista users highly recommend EasyBCD.

Follow this guide:

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by TeXtonyx on 2008-12-15
One can reinstall grub to the /boot partition also, besides lilo.
Initially, the option is at Step 7, Advanced, on the live cd.

I think your problem is coming from Windows by design putting
the boot files on just one Windows partition. If you look at
C:\ of XP and then Vista, you will likely see one of them
with all the boot files. Even though you can't boot both of
them, the other Windows installation should be viewable from
(My) Computer. XP has ntldr, ntdetect, boot.ini and Vista
has bootmgr and others I forget maybe grldr. Either XP or Vista
will have no boot files while the other one has all the boot files.

---

### Post by logos34 on 2008-12-15
> **TeXtonyx said:**
> One can reinstall grub to the /boot partition also, besides lilo.
Initially, the option is at Step 7, Advanced, on the live cd.

I think your problem is coming from Windows by design putting
the boot files on just one Windows partition. If you look at
C:\ of XP and then Vista, you will likely see one of them
with all the boot files. Even though you can't boot both of
them, the other Windows installation should be viewable from
(My) Computer. XP has ntldr, ntdetect, boot.ini and Vista
has bootmgr and others I forget maybe grldr. Either XP or Vista
will have no boot files while the other one has all the boot files.

+1 

yep, step 7 'Ready to install' screen

When you install the second windows it locates the boot files to the prexisting windows partition.

---

### Post by doyouhas on 2008-12-16
I just reinstalled grub and then copied those boot files and everything was great. Thanks to everyone with for the help.

---

