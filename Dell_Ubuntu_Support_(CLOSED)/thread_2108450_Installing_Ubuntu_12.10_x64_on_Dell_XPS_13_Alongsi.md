---
title: "Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows  from USB"
date: 2013-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lviggiani on 2013-01-24
Update - SOLUTION in post #10


Hi,
I just got a brand new Dell XPS 13 with Windows 8 preinstalled.
I would like to install Ubuntu 12.10 x64 alongside Windows 8 from USB.

I downloaded Ubuntu 12.10 and put on a USB with the ubuntu startup disk creator program.

I plugged the usb into the LH side USB port and stared the computer.
From bios setup I tryed to disable secure booting as read somewhere but it keeps booting straight into W8.
Then I enabled legacy boot order and in this way, by pressing f12 I can select USB to boot from. In this way I get a text bootloader menu and I select try ubuntu. After ubuntu desktop come up, I run the installer but when it comes to the setup mode screen, it does not detect any operating system installed and offers me to clear everything and install ubuntu.
Is this due to the fact that I booted ubuntu in legacy mode? and if so, how can I boot in uefi mode and install it alongside windows 8? the documentation that i have read says that ubuntu 12.10 should support uefi booting even if secure mode.
Can someone help me please?
Thanks in advance.

---

### Post by lviggiani on 2013-01-25
Hi, in the mean time I made some progress on this but I still have problems...

I successfully managed booting ubuntu live usb in efi mode. To do so, 

**I plugged the live USB into the lh side usb port (the rh side will not boot, no way!). Also do not use USB drive with the U3 feature as they will not be detected as bootable**

I went to bios settings and added a new boot option:

Name: usb (or whatever you want)
Device: first one listed, reading USB
File: /efi/boot/bootx64.efi

Secure boot mode is on (also tryied off)
Boot options: uefi only (legacy disable)

Whit these option, by pressing f12 and selecting USB from boot menu I sucessfully managed to get the ubuntu desktop up.

However when I run the ubuntu installer and it comes to the installation type, it keeps sayng that no other  operating system has been detected... and this is not what I want.
I happens with both the "fast/rapid start" option enabled and disabled in the bios settings.

Help please!

---

### Post by oldfred on 2013-01-25
You have to turn fast boot option off. If left on and you cannot get into Windows you may not be able to get into UEFI menu.
Best to turn secure boot off but leave UEFI boot on. Different systems do it with different settings. Some have secure boot off/on, Some have UEFI boot on which means secure boot off, but you  do not want legacy/BIOS mode on.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Grub has a bug in creating the dual boot entry for Windows, so you need Boot-Repair to create correct entries. Also if you already installed in BIOS mode Boot-Repair can convert to UEFI mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by lviggiani on 2013-01-25
> **oldfred said:**
> You have to turn fast boot option off. If left on and you cannot get into Windows you may not be able to get into UEFI menu.
Best to turn secure boot off but leave UEFI boot on. Different systems do it with different settings. Some have secure boot off/on, Some have UEFI boot on which means secure boot off, but you  do not want legacy/BIOS mode on.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Grub has a bug in creating the dual boot entry for Windows, so you need Boot-Repair to create correct entries. Also if you already installed in BIOS mode Boot-Repair can convert to UEFI mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

Hi Oldfred, first of all thank you very much for your comprehensive post.
Unfortunately I had already read most of that documentation but I still miss something... 

My current bios setting is
Intel Smart Connect Technology off
Intel Rapid Start Tecnology off
Secure Boot off
Boot menu type UEFI only

With these settings, it only shows Hard Disk and Network Boot options in the boot menu if pressing f12
So I added a boot option from the bios settings pointing to usb and setting /efi/boot/bootx64.efi

my usb has ubuntu 12.10 x64 live on it. I-ve cheched with uname -m and cat /etc/lsb_release.

Ubuntu live boots fine (I see grub 2.00-7ubuntu1). Then (here is the point where I get lost and confused) when I run the installer from the live desktop and I get to the installation type menu, I would expect and option saying that swindows 8 or other os have been detected and I can install ubuntu alongside them. Unfortunatelly I only get the option to clear the disk and install ubuntu (or manual partition mode), showing that windows 8 is not detected.

So the big point is: where do I go wrong if the installer does not detect any os already installed and offer the option to keep them?

Thanks!

---

### Post by oldfred on 2013-01-25
Intel SRT uses RAID and the Desktop installer does not have the RAID drivers. You can uninstall RAID meta data on drive.

Also turn off a fast boot setting. That by passes UEFI booting from keyboard and you can only get to UEFI menu from Windows. If Windows does not boot you may never get to UEFI to boot a repair flash drive or DVD.

       Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.


Also shrink Windows with the Windows tools and reboot a few times so it can run chkdsk and make any other fixes it does on a resize.
       
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    

            For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
    1 MB bios_grub  no format (for BIOS boot not required for UEFI)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by lviggiani on 2013-01-29
Hi, thanks again for your support.
The instructions are not that straightforward to me as I'm not so expert, however it's a good challenge to learn more.

I've read your links and done some more research. What I (believe) I understood is:


I cannot expect Ubuntu installer to recognise win 8 and install in dual boot mode out of the box like in past systems not using UEFI

The safer way to install ubuntu in dual boot mode is to relay on WIndows 8 boot loader.

Basically steps to follow are:
1) Shrink Windows 8 paritition to free some space (either from windows 8 or from ubuntu installer menu)
2) From the Ubuntu installer, when it comes to partition mode, choose manual partition mode, create a logical partition on the freed space, inside that create:
  - ext2, 250mb, mont point: /boot, primary
  - ext4, almost all free space, mount point / (you may also want to create a separate partition for /home)
  - 4Gb swap partition
3) Select the ext2 /boot partition where to install the boot loader.
4) After installation completes, the system will reboot into windows 8
5) On windows 8 download use the EasyBCD utility to create a boot entry for ubuntu

At reboot the windows 8 boot menu should allow you to boot either w8 or ubuntu.
([_[COLOR="Blue"]source[/COLOR]_]("http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/"))

Will that approach work? Even with SSD?
Thanks, Luca.

---

### Post by oldfred on 2013-01-29
With UEFI all partitions are primary.

Most desktops do not need a separate /boot.

If you only want a standard install which is fine for a new user, then auto install with just / (root) and swap is ok.

But often better to have a separate /home and a separate shared NTFS data partition.

Especially with UEFI there is no reason to use EasyBCD. In UEFI you have multiple boot loaders in the efi partition, it is like having multiple MBRs in the old BIOS configuration.

Ignore most install sites as they are referring to BIOS and MBR partitioning. If they mention logical partitions it does not apply to you. You need UEFI.

---

### Post by lviggiani on 2013-01-31
Hi Oldfred, I'm sorry for bothering you again on this but the more I read, the more I get confused...
The thing is also that I don't want to compromise my W8 installation as that is my production machine, so I'm very careful before doing anything on this.

That said, this is where I'm now:

0) I have all the intel smart/rapid/clever/super stuff off; secure boot off.

1) I have booted the Ubuntu live USB by selecting "restart" from Windows 8 while holding the shfit key down. That took me to a w8 boot menu where I selected to boot from the removable usb device.

2) At boot, the "textual boot menu" is shown and, as stated [[COLOR="Blue"]_here_[/COLOR]]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_CD_in_EFI_mode"), the fact that I see textual menu (first image) tells me that I'm booting the live installer in EFI mode. **Is my assumption correct?**

3) When I start the installer (from ubuntu live session), it says that no operating system has been detected on the computer... I though it has to do with the RAID thing. However, the posts about disabling RAID says that having RAID metadata in place prevent the installer from detecting partitions. But this is not my case... if I select "other" and I go to manual partition mode, I can see all the partitions including the EFI one, the restore etc... So, what does it mean? 
**Do I have RAID metadata or not on my SSD drive?** 
**Do I actually need to run the dmraid commands to disable RAID?**
**Removing raid metadata will compromise my Windows 8 installation?**

4) In your last post you mentioned that I can install the boot loader in the existing EFI partition. How? Just select /dev/sd1 from the drop down menu in the manual partition window of Ubuntu installer?

Let's suppose that my live session is started in EFI mode and the RAID thing is not necessary. In order to install ubuntu and reuse the EFI partition for the boot loader:
- Resize c: partition and create a / and swap in the free space
- Select /dev/sda1 (the existing EFI) partition to install the boot loader
Will that work? If not, please can you give more detailed steps?:oops:

THANKS!!!! :)
...and sorry again...

---

### Post by oldfred on 2013-01-31
Use Windows Disk Management to shrink Windows and reboot Windows a couple of times. It has to run chkdsk and maybe other fixes to update itself with its new size. Sometimes doing that outside Windows causes issues.

Also backup efi partition and Windows install. One user in another thread only did the install when Windows partitions not shown and overwrote the entire system or erased Windows. Hw ia waiting for Windows reinstall DVD from Vendor.
Ubuntu did away with the alternative installer which was for RAID and LVM installs. (server still has RAID drivers.) But all the install features were not in 12.10 Desktop installer, so perhaps parts do work?

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
I think the users with Intel SRT ran the dmraid uninstall commands to remove the meta-data to make it work. Links posted above. Some more.
       Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by lviggiani on 2013-02-01
**[SIZE="4"]SOLUTION[/SIZE]**

Here is a step by step guide of how I achieved installing Ubuntu 12.10 along side Windows 8 on Dell XPS 13 with SSD and UEFI.
I'm reporting this because as a not-so-expert user, I had to read many posts before I could feel safe trying. Maybe some other user would appreciate a step-by-step guide.

Also thanks to Oldfred and all other users posting their experience.

[COLOR="Red"]**DISCLAIMER:** you'll be playing with partitions and data you may have in your Windows 8 installation. So please DO A BACKUP before doing anything else. Also CREATE A RECOVERY USB from windows 8 dell utility in case something goes wrong. I'M NOT RESPONSIBLE FOR ANY DAMAGE OR LOSS OF DATA. IF YOU DON'T KNOW HOW TO BACKUP OR RESTORE YOUR SYSTEM, PLEASE DO NOT FOLLOW MY GUIDE![/COLOR]

And now the guide:

**BACKUP YOUR SYSTEM**
[LIST]
[*]From Windows 8, run Dell backup utility and create a rescue USB
[/LIST]

**SYSTEM SETUP**
[LIST]
[*]Reboot (or power on) the computer while holding the F12 key down. Hold it down until the menu is displayed.
[*]Use the arrow key to select "Setup" and hit enter.
[*]Move with the RH arrow to second page (Advanced) and disable Intel (R) Smart Connect Technology and Intel (R) Rapid Start Technology (use the up/down arrows to select them and the space bar to change values)
[*]Move with the RH arrow to the "Boot" page and disable Secure Boot (again up/down arrows, space bar)
[*]Press F10 and save configuration and reboot in windows 8
[/LIST]

**DOWNLOAD AND PREPARE UBUNTU LIVE USB**
[LIST]
[*][[COLOR="Blue"]_Download Ubuntu_[/COLOR]]("http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=64&release=latest") 12.10 **64Bit** from official Ubuntu site
[*]Create a bootable USB live installer as stated [[COLOR="Blue"]_here_[/COLOR]]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
[/LIST]
**Caution:** Do not use SanDisk USB keys with the U3 feature as they might not be bootable. Alternatively you may want to use the [[COLOR="blue"]_U3 Removal Tool_[/COLOR]]("http://u3.sandisk.com/launchpadremoval.htm") before creating the USB live installer

**SHRINK C:/ DRIVE TO FREE SPACE FOR UBUNTU**
[LIST]
[*]In Windows 8 perform a defrag on C:\ drive and possibly free some space using ccleaner (not required but suggested)
[*]Make sure no documents or other program is open before proceeding
[*]In Windows 8 press the Windows key and type [COLOR="DarkGreen"]cmd[/COLOR] then hit enter
[*]In the console that appears, type [COLOR="DarkGreen"]diskmgmt.msc[/COLOR] then hit enter
[*]In the Disk Management window, select the C drive at the bottom, right click on it and select "Shrink Volume" (translation may not accurate here as I've Italian version installed)
[*]Enter the space you want to reserve for Ubuntu in megabytes. I used 50Gb (50000) and confirm
[*]Once completed reboot a couple of times to see if Windows wants to run an automatic disk check
[/LIST]

**INSTALL UBUNTU**
[LIST]
[*]Insert the USB Live installer in the LH side USB port (not personally tested but I read of an user having issues starting the live media from the RH USB 3.0 port)
[*]In Windows 8 find the power off icon (i.e. hit the bottom-left corner and select settings) press it and select reboot while _holding the shift key down_
[*]Select "Use a device" (again translated from IT)
[*]Select "USB Storage Device"
[*]The system will reboot and you will see the grub textual menu. Make sure that you see the first image as stated [[COLOR="Blue"]_here_[/COLOR]]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_CD_in_EFI_mode"). **If you see the second image, stop!!!**
[*]Once the Ubuntu desktop is up, run the installer from the Desktop shortcut and follow the instructions
[*]When the installer comes to the Setup type, it will say that no operating system has been detected on the hard drive, don't worry... select "other" below and go to manual partitioning system
[*]Locate the 50GB (or whatever you've chosen) free space and create:
[*][INDENT]4000MB partition; type: swap[/INDENT]
[*][INDENT]all the remaining free space partition; type: Ext4; mount point: /[/INDENT]
[*]Select ok, make sure that the boot loader is being installed on /dev/sda and continue with normal installation
[/LIST]

**REPAIR THE BOOTLOADER**
[LIST]
[*]Once the installation is complete, the computer will boot straight into Ubuntu, not giving the option to select Windows 8. Don't panic!
[*]Log in in Ubuntu desktop, then press CTRL+ALT+T to show the terminal window
[*]Now type the following commands ([URL="https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"][COLOR="Blue"]_source_[/COLOR]
[/LIST][/URL])
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```
then
```
sudo apt-get install -y boot-repair && boot-repair
```
[LIST]
[*]Click on the "Recommended repair" and wait the program to finish
[*]Once completed, reboot your system
[*]The grub menu will appear showing some options. Select the first one reading Windows.
[*]Windows 8 loader will start and most likely here the windows disk check routine will start. If so, once completed, the system will reboot and GRUB menu will appear again.
[*]Select Windows again and check that it will start successfully.
[*]Then restart and select Ubuntu from GRUB menu and check that Ubuntu works too.
[/LIST]

[COLOR="SeaGreen"]**CONGRATULATIONS! You've now a UEFI dual boot system in place!**[/COLOR]

**FURTHER STEPS**
**Update your system**
```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Install Dell kernel patches to enable display and keyboard backlit control as well as multitouch gestures**
```
sudo add-apt-repository ppa:canonical-hwe-team/sputnik-kernel
sudo apt-get update && sudo apt-get dist-upgrade
```
Then reboot. Now you should have gestures like described [[COLOR="Blue"]_here_[/COLOR]]("https://wiki.ubuntu.com/Multitouch")

That's it! Enjoy your Ubuntu!

---

### Post by oldfred on 2013-02-01
Glad you got it working and thanks for the details.

Other will find this if they search forum and it will help them and I will link to it for others that post asking for help on a Dell.

---

### Post by lviggiani on 2013-02-01
Thanks again for your support!
Is there a way to edit my first post in this thread to add a direct link to post #10 for users looking for a solution?

---

### Post by oldfred on 2013-02-01
Because of spam you only have a limited time to edit old posts. I will add the link.

---

### Post by ATEGEV on 2013-02-16
Nice guide, lviggiani! This is the same thing I intend to for the Dell XPS 12 ([http://ubuntuforums.org/showthread.php?t=2116382](http://ubuntuforums.org/showthread.php?t=2116382)).
 
Still a few questions/remarks:

I believe that 12.10 64 bit is created to work with Secure Boot. Have you disabled it because you have ran into problems, or you just did it because they warned you for that in other topics?

Similar question for Intel (R) Smart Connect Technology and Intel (R) Rapid Start  Technology: do they need to be disabled? If yes, can they be reenabled after installation?

The Sputnik kernel is something they used to ship Dell XPS 13 laptops as developer machines in US. Lot of the ppa are uitilities for developing.
Some ppa's are for functionality. Is there a chance that some of them will corrupt my system because they specific for the XPS 13 and not for the XPS 12?

---

### Post by lviggiani on 2013-02-16
> **ATEGEV said:**
> Nice guide, lviggiani! This is the same thing I intend to for the Dell XPS 12 ([http://ubuntuforums.org/showthread.php?t=2116382](http://ubuntuforums.org/showthread.php?t=2116382)).
 
Still a few questions/remarks:

I believe that 12.10 64 bit is created to work with Secure Boot. Have you disabled it because you have ran into problems, or you just did it because they warned you for that in other topics?

Similar question for Intel (R) Smart Connect Technology and Intel (R) Rapid Start  Technology: do they need to be disabled? If yes, can they be reenabled after installation?

The Sputnik kernel is something they used to ship Dell XPS 13 laptops as developer machines in US. Lot of the ppa are uitilities for developing.
Some ppa's are for functionality. Is there a chance that some of them will corrupt my system because they specific for the XPS 13 and not for the XPS 12?

Hi,
about the secure boot, I experienced problems... If you eneable it, ubuntu will not boot as you'll ge a signature error. I tried then in boot-repair to go to advanced mode and select "secure boot". It installs the "signed" version of the linux image but then I got troubles in booting windows. Honestly I didn't investigate too much on this... I just went back to boot-repair and did the standard repair, unistalled the "signed" version of the linux image, disabled secure boot from bios and my system was dual booting again. However if you want to play a bit with boot-repair options you may be able to have secure boot working. BTW it doesn't out of the box.

The Intel smart stuff, I disabled it during installation (not 100% sure that this is actually required, but I've read everywhere to do so). Then I could re enable it and everything is working fine.

About the sputnik ppa you need it to be able to control screen and keyboard backlit as well as multi-touch. You'll see that it will only uodate kernel.
To me everythings works fine with that ppa. However do not enable the quantal-proposed ppa in software source. If you do so (at least in my experience) it will install kernel 3.5.0.24 and you will not be able to see the screen anymore (the lightness stay almost at 0 and you cannot adjoust it). With kernel 3.5.0.23 (either removing the stuff form quantal-proposed or selecting 3.5.0.23 kernel from grub menu) everything works fine. Again, I did not spent too much on this and just removed the quantal-proposed stuff.

I hope this will help.
Cheers.

---

### Post by alcyst on 2013-03-02
I followed this article & it worked well.

[http://www.calazan.com/how-to-install-the-ubuntu-12-04-sputnik-image-on-your-dell-xps-13-ultrabook/](http://www.calazan.com/how-to-install-the-ubuntu-12-04-sputnik-image-on-your-dell-xps-13-ultrabook/)

---

### Post by divydovy on 2013-04-16
Hi,

Thanks for the post @lviggiani, but it's not working for me.

I get to the hold shift/restart/select USB part and then it just boots straight back into Windows.

I've followed all the instructions and tried various combinations of things being enabled/disabled, but the only way we can get the USB to be recognised at all is to use the legacy mode boot.

Has anyone else hit this block?

Any ideas? Thanks/sorry/Linux n00b

---

### Post by lviggiani on 2013-04-16
> **divydovy said:**
> Hi,

Thanks for the post @lviggiani, but it's not working for me.

I get to the hold shift/restart/select USB part and then it just boots straight back into Windows.

I've followed all the instructions and tried various combinations of things being enabled/disabled, but the only way we can get the USB to be recognised at all is to use the legacy mode boot.

Has anyone else hit this block?

Any ideas? Thanks/sorry/Linux n00b

Hi, I suggest you to check the followings:

1) Ubuntu must be 64 bit version
2) Ubuntu must be 12.04.2 or above
3) Create the USB installer by ubuntu startup disk creator
4) Try changing the usb port (left / right)
5) Try with another USB stick (do not use sandisk cruiser usb drive with the U3 feature)

I suggest you to try different USB drives as a couple didn't work to me as well.
I hope this will help.

---

### Post by Yanick_Nedderhoff on 2013-10-15
Hey,

I'm trying to do this on my Dell XPS 12. I have no idea what I'm doing wrong. My problem is NOT that I can't install Ubuntu, but that it won't boot after install. Due to that I'm not able to to any boot repair stuff. Can somebody explain the important things so ubuntu boots after install?

---

### Post by oldfred on 2013-10-15
You can run Boot-Repair from your live installer -DVD or Flash drive. Or you can download it as a Linux repairCD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Yanick_Nedderhoff on 2013-10-16
Do I just need to post the url here or to [email]boot.repair@gmail.com[/email] as well?

[http://paste.ubuntu.com/6243800/](http://paste.ubuntu.com/6243800/)

---

### Post by oldfred on 2013-10-16
@Yanick_Nedderhoff
I actually suggest  separate threads for each different question. Only because it was also a Dell did I not create a new thread for you.

You have installed in BIOS/CSM/Legacy mode and installed grub2's boot loader to the PBR - partition boot sector of the efi partition. With a UEFI install you install grub to efi partition but it is a folder and files inside the efi partition when correctly installed.

I do not know if installing grub to efi partition's PBR will cause issues. Does Windows still boot ok? You may need to back up all the efi folders & files in efi partition (good idea to have that backup anyway). And then from live installer delete efi partition using gparted. Then recreate partition, formatted as FAT32, with boot flag, and restore backup efi files. With boot files in efi part no configuration is required. Boot files in efi partition can just be copied and restored.

You can either reinstall or use Boot-Repair to convert a BIOS boot install to UEFI boot, but in both cases have to boot in UEFI mode not CSM mode.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

How you boot installer or Boot-Repair is how it installs or repairs.
Boot-Repair is also reporting other issues.
      
>  The NTFS partition is in an unsafe state. Please resume and shutdown



You also need to turn off fast boot or quick boot in Windows and/or UEFI settings. UEFI is complex to install as there are more alternatives that must be correctly set for it to work correctly. See link in my signature for more info. But these two are the most critical to follow.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by Yanick_Nedderhoff on 2013-10-20
Hey,

thank you for your help and sorry for my late answer. I don't have that much time to deal with this problem.

There is one thing confusing me, you said

> **oldfred said:**
> You have installed in BIOS/CSM/Legacy mode

Do you mean Windows or Ubuntu? In both cases: that was not my intention. I was booting the stick in UEFI, not Legacy-mode. Maybe I made a mistake right at the beginning of the install and making that right could save me from this efi backup restore thing you explained?

EDIT: Oh, and regarding the "new post" thing. I thought it was ok because someone talked about the XPS 12 as well a few posts higher. If that's not ok I'm totally fine if someone moves this to a new thread.

---

### Post by oldfred on 2013-10-20
It looks like Boot Repair added an efi version of grub.

But you have this which is a grub BIOS boot loader installed to the partition boot sector of the efi partition:

```
sda1: __________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 469894272 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
```

---

### Post by Yanick_Nedderhoff on 2013-11-10
Hey,

again I'd like to thank you for your help. I was not able to make it work, BUT: A few days ago I tried to install the new Ubuntu 13.10, I did exactly the same as I did about 100 times before with 13.04 and it worked immediately. Can't tell why, but I'm glad it works now.

---

