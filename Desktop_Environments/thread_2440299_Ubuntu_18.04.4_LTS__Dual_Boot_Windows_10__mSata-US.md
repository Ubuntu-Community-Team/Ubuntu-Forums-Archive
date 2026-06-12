---
title: "Ubuntu 18.04.4 LTS : Dual Boot Windows 10 : mSata-USB Adapter"
date: 2020-04-08
forum: Desktop Environments
---

### Post by ketenks on 2020-04-08
I burned this version of ubuntu onto a USB and had it install the OS onto a USB-mSATA adapter with a 500GB mSATA on it. However here is the computer:

Dell Inspiron 5759
Windows 10 HDD 160GB internal

So, it normally boots up to Windows 10 but I wanted a bootable USB stick and I happened to use this USB-mSATA adapter to do it.

Ubuntu crashed because it may not have had enough space on the disk? It was working fine and then it crashed. However, the installation somehow "stole" the Windows 10 on the inside of the computer for itself and what I mean is, that I could no longer boot natively to Windows 10 anymore without having the USB-mSata hooked up. 

So when Ubuntu crashed, so did my ability to get to Windows 10 because I had to use the usb stick to get there.

In the BIOS, it was strange. Originally I had it boot to USB but after the installation, the BIOS had moved the boot order around and it somehow thought that this USB-mSata adapter was actually the "Internal HDD" that it was trying to boot from.

So now, it's looking for this USB stick when it tries to boot from the "Internal HDD" from the BIOS and it gives this error exactly:

```
error: no such device: 3c31e8af-a9f6-486b-953e-1e462d589854
error: unknown filesystem.
Entering rescue mode...
grub rescue> _
```

I have flashed the Dell Inspiron 5759 with the original BIOS through another USB and the F12 options. No change was made to this error. It's still looking for the mSata adapter as the Internal HDD somehow...

Oh yeah, I also thought that maybe reinstalling Windows10 would reset the file systems back to normal but when I restarted it gave this same error. So now, my Win10 internal is in limbo waiting to be reinstalled...

---

### Post by oldfred on 2020-04-08
Your system is UEFI.
Did you install in UEFI boot mode?

Most Dell need UEFI update, and if SSD, SSD firmware update. And that may reset UEFI settings to defaults, so any you change need to be checked and redone.
And drives changed from RAID/Intel RST to AHCI. Install Windows AHCI drivers first if you still want Windows.
Windows fast start up must be off.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Issues with Dell are common across many models. These may have similar issues.
Dell 5500 
[https://ubuntuforums.org/showthread.php?t=2436198](https://ubuntuforums.org/showthread.php?t=2436198)
 Dell Inspiron 5491
[https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes](https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes)
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)

---

### Post by ketenks on 2020-04-08
It's a UEFI but it only allows "Legacy Boot Option". I haven't been able to use the UEFI within this BIOS for some reason. I've tried changing the options to get it to do the UEFI but to no avail. It just says it's not allowed for some reason.

I'll try the boot repair.

---

### Post by CelticWarrior on 2020-04-08
> **ketenks said:**
> It's a UEFI but it only allows "Legacy Boot Option". I haven't been able to use the UEFI within this BIOS for some reason. I've tried changing the options to get it to do the UEFI but to no avail. It just says it's not allowed for some reason.

I'll try the boot repair.


Yes, please try Boot Repair but NOT to try to repair, only to generate the summary report so we can see what's going on.

Furthermore you need to understand UEFI and this is not nitpicking with terminology.
UEFI is what replaced BIOS a long time ago. Many people still use the terms interchangeably, including vendors, but that's wrong. UEFI isn't BIOS, BIOS isn't UEFI, if you have one you don't have the other. However, many UEFIs still have/allow a compatibility mode for OSes that don't support UEFI (AKA "Legacy"/"CSM"/"BIOS mode", etc.). That's your "Legacy Boot Option". 
Any modern OS - from the last decade or so -, Windows or desktop Linux, supports and should be installed in UEFI mode which, conveniently, is very useful and easier to manage in dual-boot. Now, if the previous OS has been installed in "Legacy mode" (for no good reason, of course) and you don't want to reinstall it properly, then install the second (or third or...) OS in the same mode, otherwise you won't be able to dual-boot the normal way, only by changing mode in UEFI ("BIOS") each time you want to boot a different OS.

---

### Post by ketenks on 2020-04-08
I did know those things. It is UEFI and it is stuck in "Legacy Boot Option". I am trying to dual boot and it is messing up. My thought was that it would either boot from USB or from Internal HDD but for some reason, the USB-mSATA adapter has made it such that the Internal HDD is now that USB port from where I originally booted it from. That was how I was going to dual boot. And now it is messed up because ubuntu crashed. However, even if ubuntu didn't crash, I was no longer able to boot natively to the Windows 10 internal HDD. I had to have the USB-mSATA adapter in order to boot from it ever since I installed the ubuntu into the adapter.

And I just burned the boot repair iso onto a flash drive and it is not booting up from USB. It's just hanging with the flashing _.

---

### Post by CelticWarrior on 2020-04-08
That's why we need the summary report. It show us what the users don't understand or can't explain properly.

---

### Post by oldfred on 2020-04-08
Microsoft requires vendors to install in UEFI mode to gpt partitioned drives since 2012 with release of Windows 8.
Somewhere your system had settings to allow or require UEFI boot.

Some older Dell seemed to need Legacy enabled, but set boot to UEFI. Newer systems need legacy turned off.
My old Haswell based Dell. has these settings.
Under Advanced: USB enable, On board device, AHCI.
Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode UEFI.
But then every USB installer has two boot modes UEFI:flash or flash where flash is name or label of flash drive. And one with just name is the BIOS/legacy/CSM boot mode.

Some tools that create live installer, only install it in one boot mode or the other. Often a user changes flash drive, changes which installer used or other changes and happens then to create it in dual boot mode and it then works.

I have seen posts with Rufus where it has MBR & CSM(UEFI) or gpt & UEFI. Note that CSM is BIOS boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by ketenks on 2020-04-08
I've reburned the ISO boot repair onto the flash drive using UNETBOOTIN because I am on a MAC. After restarting, on my Dell it is still hanging on the _.

---

### Post by ketenks on 2020-04-08
Im actually concerned, that even if I were to reinstall windows from USB onto my Internal HDD, that I would not be able to boot from it because of whatever ubuntu did to the paths in the bios that seem to be persistent even after flashing the BIOS with the original Inspiron5759_170.exe...

---

### Post by CelticWarrior on 2020-04-08
> **ketenks said:**
> Im actually concerned, that even if I were to reinstall windows from USB onto my Internal HDD, that I would not be able to boot from it because of whatever ubuntu did to the paths in the bios that seem to be persistent even after flashing the BIOS with the original Inspiron5759_170.exe...


Such concern is unwarranted. And again, you have UEFI, not BIOS. And no, OSes don't do anything to the "paths" (whatever that is)... 
You really need to understand UEFI, how it boots and its requirements (some already explained in the post above by oldfred).

Also, regarding Boot Repair, olfred in post#2 **explicitly told you NOT to use the old ISO**: > May be best to see details, **use ppa version with your live installer  (2nd option) or any working install,  not older Boot-Repair ISO** and that meas booting the Ubuntu installer and **installing Boot Repair in the live session** using the instructions provided in the Boot Repair's page.

---

### Post by ketenks on 2020-04-08
Ok for whatever reason, messing with things its all come back alive. However the windows 10 still wont boot natively. The ubuntu is now working again for some reason and the windows 10 does boot up from the ubuntu grub screen but windows 10 is on the internal HDD and it won't boot up without having the mSATA adapter plugged in.

---

### Post by CelticWarrior on 2020-04-08
That means you have both OSes in "legacy mode" and the bootloader has been installed in the external drive.

---

### Post by ketenks on 2020-04-08
The UEFI is in "legacy mode" I've never set anything about the installations. I've never done anything but run the default ubuntu installation and the default windows 10 installation. I've never set anything about that. The BIOS of this Dell is stuck in "legacy mode" and I've never been able to change it. So the OSes must have seen that in the BIOS and done whatever necessary to install.

Now how do I get my Windows 10 internal HDD OS to be bootable again, while ubuntu, on the mSATA adapter, is not plugged in?

---

### Post by CelticWarrior on 2020-04-10
You may try installing Grub in the MBR of the internal drive and then change thte boot order to that one. 

PS - I really doubt your UEFI (Again, UEFI IS NOT BIOS) is stuck in legacy mode. If it really is your firmware is broken. Of course, with a setting such as "legacy mode" all OSes were installed in such mode and that is the root of your problem.

---

### Post by leok2 on 2020-04-10
Might be a good idea to see the Dell support site if you think there is a problem with the BIOS settings..here is a link to common problems:

[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)

---

### Post by ketenks on 2020-04-10
The Dell UEFI is called BIOS by the Dell itself. It's also one of the worst I've seen. It does not have any other option than one "Internal HDD" because that is all that it has hardware wise. Once I installed a full OS inside of a USB then it thought that USB was now the "Internal HDD". Somehow, the reference to the original "Internal HDD" was switched to the USB from within. 

I've flashed the UEFI to the original UEFI from the Dell website and I still have the same issue of there being no way to boot from windows without having the ubuntu do it itself.

Since I flashed the UEFI, it does allow me to enable the UEFI boot option. However it only gives 2 options: the Onboard NIC IPV4 and the Onboard NIC IPV6 options. When trying to add anything to it, it says "No Filesystem found."

It also can't find the windows on it's own when I try to boot up  with the UEFI option. It says that it cannot find any file system. So I had to switch back to BIOS Legacy Mode and boot from the USB-mSata adapter ubuntu os and I'm still here doing that.

Somehow, the installation of Ubuntu has changed the original nature of how this computer boots up because neither the BIOS or UEFI options will boot anymore to the Internal HDD Windows 10 that was already there. (except when done through the ubuntu)

---

### Post by CelticWarrior on 2020-04-10
OSes installed in legacy mode can't be booted in UEFI mode, they must be **installed **that way. And Windows strictly requires GPT for UEFI and MBR for BIOS/Legacy. That's why it doesn't find any to boot from. You really need to start understanding this things.

---

### Post by ketenks on 2020-04-10
Yeah but that's not the issue at all here. The issue is that before it was booting in BIOS mode just fine until I installed ubuntu on a USB-mSata adapter. You need to start understanding this.

---

### Post by CelticWarrior on 2020-04-10
> **ketenks said:**
> Yeah but that's not the issue at all here. The issue is that before it was booting in BIOS mode just fine until I installed ubuntu on a USB-mSata adapter. You need to start understanding this.

No, I don't need to start understanding it because a) I already do (and already explained WHY - post #12) and b) it's not my problem, **it's yours** (I never had such problems because I know what I'm doing in single, dual or multiple booting, in BIOS or UEFI systems), and you don't know enough to even understand what happened (again #12).

I wouldn't expect you to know HOW to solve it but at least understand the basics and the options to move on from where you currently are. And those options are your choice to make.

---

### Post by ketenks on 2020-04-10
Why would dual booting from BIOS mode make it to where I can no longer boot from windows 10? That's a problem with the ubuntu installation. Before ubuntu I could boot from the BIOS mode just fine. After ubuntu I can not. So ubuntu changed how the boot is working at all. What is that change and what is the solution?

---

### Post by CelticWarrior on 2020-04-10
> That means you have both OSes in "legacy mode" and the **bootloader has been installed in the external drive**.

The "bootloader" is Grub and it was **probably** installed in the external drive because you changed the default location which is typically the first drive detected, not necessarily the one where the second OS is installed. It's bloody obvious to anyone knowing the basics. And no, even that it's not "a problem with the ubuntu installation", it's a problem with the selctions that were made during the installation.

And how to correct it is not that hard. From post #14: > try installing Grub in the MBR of the internal drive and then change the boot order to that one which means exactly that, install Grub to whatever drive is the internal one and then, obviously keeping the settings in UEFI as "Legacy", change there the boot order making the whatever drive the first in the boot order. This is if you want to keep everything "legacy". I definitely wouldn't. Now that the proper UEFI mode is available I would reinstall everything in UEFI mode and benefit from the huge advantages it brings, particularly for multi-booting OSes.

---

### Post by mc4man on 2020-04-10
It's been a while since I tried what you did so maybe things have changed.
If not, then what's happening is to be expected when you install ubuntu to an external device in the presence of the existing install. Now you need the external connected to boot up.

Myself have an external usb ssd ubuntu install that's 'self contained'. If I boot the laptop up without it it goes directly to win10, if it's connected I go to the grub screen, ect.
 Have done 2 different ways on laptops - 

One way was to 1st use gparted to disable the boot and esp flags on the internal drive, create an EFI System partition on the external drive. Then install ubuntu and bootloader to the external.. When done re-enable boot/esp flags on internal.
 Second (current way), I took an unused but EFI  laptop, removed all partitions on the internal, then use it to install to the external.

What's sudo blkid show?

---

### Post by CelticWarrior on 2020-04-10
> **mc4man said:**
> One way was to 1st use gparted to disable the boot and esp flags on the internal drive, create an EFI System partition on the external drive. Then install ubuntu and bootloader to the external.. When done re-enable boot/esp flags on internal.
 Second (current way), I took an unused but EFI  laptop, removed all partitions on the internal, then use it to install to the external.


That's a way indeed, but for UEFI. The systems are installed in legacy/MBR so... The only way to achieve the same would be booting Windows media in order to reinstall the Windows bootloader to the internal drive and adjust the legacy boot order accordingly *only* when the OP intended to boot Ubuntu.

---

### Post by ketenks on 2020-04-26
Ok, so I looked into everything you guys have said and I saw that the least path to resolving the issue was to simply do a fresh install of everything but when I install Linux I go ahead and remove the internal HDD so that it doesn't steal anything from it when installing. 

So this is what I did. I backed up my files, and did a fresh install to the internal HDD with a bootable Windows USB *after* I had flashed the BIOS a second time so that it was not corrupted from anything in the Ubuntu installation. Then I removed the internal HDD and did a fresh install of Linux Mint Cinnamon and this time, I could do the whole install to the USB-mSATA adapter as though it were really just a USB and not some internal part of the computer. 

And it worked! I can now boot from Windows while the USB-mSATA adapter is not plugged in, and it will boot from the adapter when it is plugged in because in my BIOS it is setup to boot from USB before the Internal HDD. Great.

Lastly, this BIOS does not truly support UEFI and on the official page of the Dell laptop's-BIOS-flashing-driver-utility page, they call it a BIOS both on the page and within this computer's own flashing process. There was truly no option to boot from UEFI within this BIOS because every time I tried to add a boot option while within that mode it would only say, "File system not found!" and give me no other option to do anything. 

But it works now after having flashed the BIOS, doing fresh install of Windows and then a fresh install of Linux while the internal HDD was removed from the computer. Thanks for all your help.

---

