---
title: "Booting Windows only if USB flash disk is plugged in."
date: 2020-08-12
forum: Desktop Environments
---

### Post by johncooool on 2020-08-12
This is the 2nd post this year about the same subject. I am working on it with "oldfred". oldfred has asked me to open a new thread (I am also the thread starter last time) to work on it. It was solved last time under some different circumstances. The solution can be found at [https://ubuntuforums.org/showthread.php?t=2429070&page=3&p=13979067#post13979067](https://ubuntuforums.org/showthread.php?t=2429070&page=3&p=13979067#post13979067)

The method worked on Legacy support motherboard of a laptop running Win7 and now I am trying it on a UEFI motherboard of a laptop running Win8.1 .

I did the same steps except for one of them all listed here below. 


[LIST]
[*]Run a repair after booting into "Boot repair disk" to install MBR files that the Grub menu will see.
[*]Create a USB disk to boot up Grub menu. The Grub menu used is from Super GRUB2 Disk
[*]Make C: partition inactive from Diskpart so that windows will no longer load without the USB being plugged in to choose it from the grub menu. (I did not deactivate the grub until it works before making it inactive)
[/LIST]

Hibernate does not work because main Win C: partition is made inactive. But Sleep still works...

It did not work on the newer motherboard using UEFI. I can still see all the partitions and I tired all the options and it just gives an error message.

---

### Post by oldfred on 2020-08-12
With UEFI, you do not use MBR.
UEFI uses gpt partitioning, but has a protective MBR, just with one gpt partition table entry. That is so old versions of partition tools see that drive is partitioned and do not immediately try to partition it.

UEFI is a lot different than the 35 year old BIOS/MBR configuration.
Windows only boots, installs or repairs UEFI systems when you have gpt partitioning.

You must always boot installers in UEFI mode, not BIOS/CSM/Legacy mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

What brand/model system? What video card/chip?

Lot more general UEFI info in link in my signature below.
But some systems need boot parameters or settings in UEFI.

Have you updated UEFI to latest available by your system vendor?

---

### Post by johncooool on 2020-08-13
If it it cannot be done then no need to try it... If it can be then I will try it. 
Does the solution have to be tailored for each device? If so then it won't be worth it...

The benefit of the other solution is that it was very easily reversible. Will this be easy to reverse it?

I did do a BIOS update to the latest version which I assume is the same one for UEFI.  

The system is: Lenovo G50-80 Laptop Running Win 8.1

Why is the Video card information needed?

Video card info is:

```
Display Devices
---------------
          Card name: Intel(R) HD Graphics Family
       Manufacturer: Intel Corporation
          Chip type: Intel(R) HD Graphics Family
           DAC type: Internal
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_8086&DEV_0A16&SUBSYS_390B17AA&REV_0B
     Display Memory: 1920 MB
   Dedicated Memory: 128 MB
      Shared Memory: 1792 MB
       Current Mode: 1366 x 768 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: unknown
         Monitor Id: LGD0468
        Native Mode: 1366 x 768(p) (60.005Hz)
        Output Type: Internal
        Driver Name: igdumdim64.dll,igd10iumd64.dll,igd10iumd64.dll,igdumdim32,igd10iumd32,igd10iumd32
Driver File Version: 10.18.0014.4264 (English)
     Driver Version: 10.18.14.4264
        DDI Version: 11.1
     Feature Levels: 11.1,11.0,10.1,10.0,9.3,9.2,9.1
       Driver Model: WDDM 1.3
Graphics Preemption: Primitive
 Compute Preemption: Thread group
           Miracast: Supported
Hybrid Graphics GPU: Integrated
     Power P-states: Not Supported
  Driver Attributes: Final Retail
   Driver Date/Size: 8/9/2015 04:52:04, 25076864 bytes
        WHQL Logo'd: n/a
    WHQL Date Stamp: n/a
  Device Identifier: {D7B78E66-4956-11CF-B264-0519B6C2C735}
          Vendor ID: 0x8086
          Device ID: 0x0A16
          SubSys ID: 0x390B17AA
        Revision ID: 0x000B
 Driver Strong Name: oem44.inf:5f63e5341cc65b69:iHSWM_w81:10.18.14.4264:pci\ven_8086&dev_0a16
     Rank Of Driver: 00DA2001
        Video Accel: ModeMPEG2_A ModeMPEG2_C ModeWMV9_C ModeVC1_C 
        DXVA2 Modes: DXVA2_ModeMPEG2_VLD  DXVA2_ModeMPEG2_IDCT  DXVA2_ModeWMV9_IDCT  DXVA2_ModeVC1_IDCT  DXVA2_ModeH264_VLD_NoFGT
```

---

### Post by oldfred on 2020-08-13
Without knowing video, do not know if any of these apply:
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
Some chips like nVidia need nomodeset boot parameter. Now Ubuntu offers to install proprietary driver as part of install, so boot parameter not required on first boot, just on installer or safe boot option.
Just then needed to know it was Intel  and that normally just works.
Lenovo laptops containing Optimus graphics W520/T520/T530 nox2apic boot parameter
[https://gist.github.com/wbond/3800562](https://gist.github.com/wbond/3800562)
[https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot](https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot)

When I looked up specs for your model, it says Graphics. Graphics Processor. AMD Radeon R5 M330
So even looking up specs does not always match actual system configuration.

Most vendors have families of models that have similar issues & solutions.
But Lenovo seems to have many models and they all seem to be different.

Old thread says your model had issues with Wi-Fi. Not sure if not resolved as newer versions of Ubuntu fix many things. If not see this:
[https://ubuntuforums.org/showthread.php?t=2297603](https://ubuntuforums.org/showthread.php?t=2297603)

Are you booting in UEFI mode?
What error code do you get.
Have you installed & its not booting. Then post link to summary report from Boot-Repair.

---

### Post by johncooool on 2020-08-13
Your knowledge of Hardware is very impressive. It is almost like you are one with it. You probably posses superior memory.

I do not have any known issues with the device. WiFi or otherwise but thanks for the consideration.

Yes it does have legacy support but I am booting in UEFI and windows works normally on it.

The only Linux I have is the Grub menu I use to login like I did before (in the old thread).

I prepared the Grub menu form Supergrub 2 with Rufus and as I prepare it. It gives option to prepare the USB for UEFI and for BIOS.

When I set the setting to login with Legacy support it boots into Grub menu normally but when I set it purely on UEFI it will see the USB in bootup menu but will not boot into it. It will skip over it and continue to Windows.

Last time other Grub menus did not work. Maybe the solution is to use another one once again. Maybe if the USB boots into UEFI then it will work.

I will get the error message when trying to login to Windows via USB Grub menu.

---

### Post by oldfred on 2020-08-13
Do you have Windows fast start up off?
Grub only boots working Windows. So no hibernation (fast start up sets a hibernation flag), nor any other issues like chkdsk required.

Are you getting grub menu which is UEFI boot or the purple BIOS boot screen?

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
More info on Windows:
[http://www.eightforums.com/](http://www.eightforums.com/)

Memory not so good anymore. But common questions saved into Zim file which is easy to locally search.

---

### Post by johncooool on 2020-08-13
I am not using Fast boot but there is an option in the BIOS called fast boot. It might be on.

Will Check disk stop working if booting without flag?

I am not getting a purple menu. It is in orange color.

I will add a link that has a video of the process to get all your answers.

---

### Post by CelticWarrior on 2020-08-13
Fast Boot is a UEFI ("BIOS") feature; Fast Startup is a Windows feature. There's a big difference. Anyway, you want both disabled for better results.

---

### Post by oldfred on 2020-08-13
The fast boot is an UEFI setting, where system assumes no changes and does not do POST or scan of system for your configuration. Often then you do not have time to press any key before default boot starts. While reconfiguring best to have off. 
The fast start up is a Windows setting that uses a type of hibernation. That must be off for the Ubuntu NTFS driver to see NTFS partitions in normal read/write mode and for grub to boot Windows.

With UEFI, the boot/esp flag(s) must be on the ESP - efi system partition or the FAT32 partition. Only one per drive and Ubuntu & Windows will share the one on your first drive.

---

### Post by johncooool on 2020-08-13
No video but the link contains Pictures for assistance.

[https://www.dropbox.com/sh/7709q2b41hk4i09/AABlKNW6Zw0ZBJYCIEWaTW5ha?dl=0](https://www.dropbox.com/sh/7709q2b41hk4i09/AABlKNW6Zw0ZBJYCIEWaTW5ha?dl=0)

You can skip sign up if it is requested from you and get to the photos.

---

### Post by oldfred on 2020-08-13
Most systems require you to have UEFI first or UEFI only setting. A very few seemed to need legacy on, but UEFI still set as default boot.
My Asus motherboard would not boot in UEFI mode, even with 'UEFI or Legacy' mode. The only UEFI mode that worked was 'UEFI only'.

You are using Supergrub, not grub. That is why you have an orange background. Not sure then if it is trying to boot in BIOS or UEFI mode. But UEFI and BIOS are on compatible. Once you start booting in one mode or the other, you cannot switch mode. Or grub only boots other installs in same boot mode.
A few boot loaders can take advantage of UEFI's one time reboot feature to reboot into another boot mode. Grub does not.

Grub only boots working Windows. So boot Windows from UEFI boot menu in UEFI mode, must have legacy off. Then fix Windows.

---

### Post by johncooool on 2020-08-16
I tried to create the supergrub with Rufus to boot while in pure UEFI mode. Now the option is there in Rufus and it works with Win8.1 installation media but it did not work with SuperGrub.

I will search for other methods.

---

### Post by johncooool on 2020-09-11
I managed to create a USB flash disk with super grub 2 on UEFI and I got errors. It works when secureboot is disabled from UEFI/BIOS

I added the image to view the errors.

[https://www.dropbox.com/s/nzczfkb8kv4yy18/dsc_0001.jpg?dl=0](https://www.dropbox.com/s/nzczfkb8kv4yy18/dsc_0001.jpg?dl=0)

This is on NTFS and I got similar error on FAT32

---

### Post by oldfred on 2020-09-11
I know grub had issues booting Windows if UEFI Secure boot on.
I expect Supergrub to have same issue as related to the chain of trust and use of UEFI keys.

---

### Post by johncooool on 2020-09-11
OK, Is there a known solution?

Is there hope? can it be done?

---

### Post by johncooool on 2020-09-11
I am guessing that it can only work on Legacy support systems.

Can Win 8 and 10 be installed like that so that the idea will work?

---

### Post by oldfred on 2020-09-11
Leave UEFI secure boot off.
Then grub should boot it, it Windows boots directly from UEFI.
You may have Windows fast start up on. That must be off for grub to boot Windows as it sets hibernation flag and then the Linux NTFS driver will not mount your NTFS partitions. Or did you convert to dynamic partitions in Windows, that would be a major issue.

If you only have one drive, converting to BIOS/MBR makes for a huge hassle.
Windows only boots in BIOS/legacy/CSM mode from MBR partitioned drives. And then you only have one MBR. So have to have grub in MBR to dual boot. And conversion  from/to MBR or gpt erases drive. There are some tools that may convert a drive, but partition requirements are a lot different for Windows UEFI or BIOS.

But grub only boots working Windows, so when Windows does an update, you have to temporarily install a Windows boot loader, fix Windows, and then restore grub.
With UEFI, you often can directly boot Windows from UEFI boot menu and make whatever changes or fixes are required. 

But still best to have both Windows repair flash drive and Ubuntu live installer to make repairs if needed.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by C.S.Cameron on 2020-09-11
The method many Linux users use to only boot Linux when a USB stick is plugged in, is to install Linux on a USB stick.
With Rufus you can install **Windows to Go** on a USB stick. Windows to Go is a Full working install of Windows. This method will insure that Windows will only boot when the stick is plugged in.

---

### Post by johncooool on 2020-09-12
> **C.S.Cameron said:**
> The method many Linux users use to only boot Linux when a USB stick is plugged in, is to install Linux on a USB stick.
With Rufus you can install **Windows to Go** on a USB stick. Windows to Go is a Full working install of Windows. This method will insure that Windows will only boot when the stick is plugged in.

Not a bad Idea... Thanks for the tip.

I am just doing this as a fun project. 

It works well on the old system running Windows. Does not matter much if it won't work well on newer systems.

USB raptor is a very powerful security system I can use that if I cannot find the solution.

---

### Post by johncooool on 2020-09-12
> **oldfred said:**
> Leave UEFI secure boot off.
Then grub should boot it, it Windows boots directly from UEFI.
You may have Windows fast start up on. That must be off for grub to boot Windows as it sets hibernation flag and then the Linux NTFS driver will not mount your NTFS partitions. Or did you convert to dynamic partitions in Windows, that would be a major issue.

If you only have one drive, converting to BIOS/MBR makes for a huge hassle.
Windows only boots in BIOS/legacy/CSM mode from MBR partitioned drives. And then you only have one MBR. So have to have grub in MBR to dual boot. And conversion  from/to MBR or gpt erases drive. There are some tools that may convert a drive, but partition requirements are a lot different for Windows UEFI or BIOS.

But grub only boots working Windows, so when Windows does an update, you have to temporarily install a Windows boot loader, fix Windows, and then restore grub.
With UEFI, you often can directly boot Windows from UEFI boot menu and make whatever changes or fixes are required. 

But still best to have both Windows repair flash drive and Ubuntu live installer to make repairs if needed.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)


I did not understand your tips very well. I am not going to try installing Win8 on MBR system. I just want to know if it works. I want to know if Windows 8.1 and Windows 10 can work on MBR so that the same process that I used on Win 7 can work here too.

FastBoot is off.

It does login into Grub if I am using Legacy support with MBR support.

It gives the error in the image provided earlier when I prepare the Grub using GPT support for UEFI.

---

### Post by oldfred on 2020-09-12
Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR partitioned drives.
Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 released in 2012.
The BIOS mode was for large corporations that had BIOS systems and wanted to install newer Windows.

Intel publishes future configuration specs. Several years ago it wanted manufacturers to make systems using UEFI type 3 which has no CSM. Saves the extra chip to implement CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Then they suggested elimination of CSM, by 2020, but have not seen any systems yet. I believe they again published future specs but further in future for UEFI type 3, elimintion of BIOS mode.

While Ubuntu ISO can be booted in UEFI or BIOS/CSM/Legacy mode, I believe Rufus only makes the installer one or the other. Most tools to create USB/DVD installer will boot either way from UEFI boot menu, if settings in UEFI allow it. If Secure Boot is on, only UEFI Secure boot is allowed and you normally have to also turn on allow USB boot as that also for security.

---

### Post by johncooool on 2020-09-12
So then according to the last post this is the easy solution.

Install Windows 8.1 on MBR and not GPT (GPT is the default for new systems) and then follow the same solution mentioned that works on BIOS system.

The link for the solution that works and I use on my Windows old system running windows 7 is: [https://ubuntuforums.org/showthread.php?t=2429070&page=3&p=13979139#post13979139](https://ubuntuforums.org/showthread.php?t=2429070&page=3&p=13979139#post13979139) 

If some motherboards don't support the requirements then it might not work.

I found the below video of someone booting Windows 10 from SuperGrub. I downloaded the exact same version Rufus only sets it up for UEFI which is good news.

However, I still got the same errors posted before when I tried to boot into it. I tried with a couple of more different settings but no luck yet. I will try a few different versions that are for UEFI. Some of the people who commented on the video seem to have gotten it to work...

Maybe one will work. 

[https://www.youtube.com/watch?v=7JfU2lFucgQ](https://www.youtube.com/watch?v=7JfU2lFucgQ)

None of the versions worked.

All gave the same error.

---

### Post by oldfred on 2020-09-14
What versions, what errors?

And what partitioning do you already have on drive?
sudo parted -l

Grub only boots working Windows, I would think then Supergrub would be same way.

If Windows errors you typically have to use your Windows repair flash drive to fix Windows.
With UEFI you may be able to directly boot Windows and f8 as booting, get into the internal repair console.

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Rescatux live cd with a grub restore option (through rescueapp) fixed it!
Will now repair Windows BIOS & UEFI
[https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot](https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot)

---

### Post by johncooool on 2020-09-14
It seems that you completely forgot my request, maybe because it has been so long.

Forget about windows and other.

I am unable to boot supergrub while in UEFI mode. I found the below video in the below link of someone who got it to work but it does not work for me.

[https://www.youtube.com/watch?v=7JfU2lFucgQ](https://www.youtube.com/watch?v=7JfU2lFucgQ)

I just need it to boot the same way.

It works well in Legacy support mode. but does not work in UEFI mode.

Error are same like in the link: [https://www.dropbox.com/s/nzczfkb8kv4yy18/DSC_0001.JPG?dl=0](https://www.dropbox.com/s/nzczfkb8kv4yy18/DSC_0001.JPG?dl=0)

---

### Post by oldfred on 2020-09-14
The unknown file system is often just Windows fast start up on which sets the hibernation flag, preventing the Linux NTFS driver from seeing the NTFS partitions. Or chkdsk required if NTFS or fsck if ext4 formatted.

I used to use to use Supergrub with BIOS for emergency boot, but have used rEFInd with UEFI for emergency boot. I have multiple repair flash drives and still have Supergrub and Rescatux on some of them. I typically boot ISO, so I can have more than one system on one flash drive.
But normally use grub2 for booting my installed systems.

---

### Post by johncooool on 2020-09-14
I don't have fast boot on.

I removed the hard drive to test if it would boot without it, but I got the same error when in UEFI mode.

It only works in Legacy mode.

I don't have a problem using Grub instead of Super Grub.

But I am unable to find a place to download a standalone Grub menu.

Is there a location I can download one for testing?

---

### Post by oldfred on 2020-09-14
I have installed grub to flash drives just for booting  ISOs. But always from a working install of Ubuntu.

You can download grub, but have to compile it yourself, then.

---

### Post by johncooool on 2020-09-15
Is it possible for you to create one for me and send me a download link from you cloud?

I am not skilled at such things.

I don't know how to code...

---

### Post by johncooool on 2020-09-15
If not then maybe we can check if the code in supergrub is not the issue. But I don't know how to do that...

Any tips on that?

---

### Post by oldfred on 2020-09-15
I only know a little python, anymore.

Fast boot is a setting in UEFI. Assumes no system change & immediately boots. Can be so quick you do not have time to press a key to get into UEFI or UEFI boot menu. Normally full cold boot/shutdown & total restart then works to be able to press a key.
Fast start up is a setting in Windows. Then Linux NTFS driver then cannot see NTFS partitions and grub will not boot Windows.
Both should be off. 
And the Windows setting gets turned back on with Windows updates.

Are you not able to boot Windows from UEFI boot menu?

---

### Post by johncooool on 2020-09-15
Fastboot is off in Windows and in UEFI/BIOS. SecureBoot is also off in UEFI/BIOS.

As mentioned before, I removed the Drive completely to test if it is causing that issue and I still got the same errors I sent it here before.

As you can see in the errors. [https://www.dropbox.com/s/nzczfkb8kv4yy18/DSC_0001.JPG?dl=0](https://www.dropbox.com/s/nzczfkb8kv4yy18/DSC_0001.JPG?dl=0)

Does this site have chat? Can I get live assistance to eliminate all problems because it seems like we are not moving ahead? I can boot up the system while live on camera.

Windows has no issues booting at all.

---

### Post by oldfred on 2020-09-15
But it is not seeing your NTFS partitions. And that is a Windows issue. 
Are you sure Windows fast start up or hibernation is off.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) & 
[https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by johncooool on 2020-09-15
I am 100% sure about fast startup. It is off for sure. I also mentioned that I removed the drive from the laptop and still did not work. It only works in legacy support mode. I checked it several times. Even before the last post. It is off.

But I don't know about hibernation. I don't use it.

I never new it can be turned off.

Do I have to turn it off?

That is mine on win8.1

[https://www.dropbox.com/s/6mbvl2cj2zm3bxq/1.PNG?dl=0](https://www.dropbox.com/s/6mbvl2cj2zm3bxq/1.PNG?dl=0)

The below is some information about the partitions on my drive. I did not create them. They are created by Lenovo.

[https://www.dropbox.com/s/qeas6ruuertgmdy/Capture.PNG?dl=0](https://www.dropbox.com/s/qeas6ruuertgmdy/Capture.PNG?dl=0)

---

### Post by oldfred on 2020-09-15
Standard set of Windows partitions for UEFI/gpt.

You need hibernate off also.

---

### Post by johncooool on 2020-09-15
Disabling hibernate did not work either.

Anyway, I posted a request with Supergrub Forum on Github.

If it still cannot be solved then I will will just close the thread.

---

### Post by johncooool on 2020-09-19
I did not get a response from any of the other forums on booting SuperGrub errors on UEFI.

Even if it did work. It would still not be convenient. Unlike my other system (Legacy support BIOS running Windows 7) where I am using it in every boot up. The solution for that can be found in a link in the 1st post of this thread. On the UEFI system it never remembers the boot order, so each time I have to go to boot menu. To access the Boot Menu I have to press a small button on the side of the laptop, unlike in old systems where all these things where much easier. It also has an issue detecting the attached USB so I would have to keep turning it off and pressing the small button on the side. I have to keep on doing that over and over until it detects the connected USB.

So over all the solution is not hassle free. 

I think the best solution for this is to install the system with MBR instead of GPT. Maybe one day I will do that and test it on legacy support and update here. But I am not planning to do so.

Even if it work it won't be convenient because it does not remember the boot up settings mentioned above in this post.

---

### Post by oldfred on 2020-09-19
UEFI boots external devices from /EFI/Boot/bootx64.efi. Which is usually shimx64.efi with Ubuntu and whatever .efi file Windows uses to boot with. Not sure Windows can boot an internal install from external device.

If you have a standard entry like "grub" or "ubuntu" in UEFI for an external drive, it will forget that entry when device is unplugged.

I have put a full install of grub into a flash drive and manually edited grub to loopmount ISO. So it can be customized, but with a grub install without full Ubuntu everything is manual.

---

### Post by johncooool on 2020-10-02
I recently upgraded Windows 7 to Windows 10 on the system running with Legacy Support.

The same process in the link of the 1st process dedicated to that method has worked well.

So in conclusion. Install Windows on Legacy support if possible to get this secure way to work.

---

