---
title: "Upgrading BIOS version on a Dell Inspiron 6400 without battery"
date: 2013-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eDFPxpX on 2013-10-12
SOLUTION: [http://ubuntuforums.org/showthread.php?t=2180265&p=12884863#post12884863](http://ubuntuforums.org/showthread.php?t=2180265&p=12884863#post12884863)
_____________
My father's laptop is running Windows XP which is going to be unsupported in a matter of months. I want to upgrade the BIOS of the laptop as the current BIOS version can't run any newer Windows version. I know I can upgrade the BIOS using Windows but it requires a battery (ours is dead) to upgrade. 


But I found this guide to help me upgrade the BIOS: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)


I am a bit familiar with Linux command line interface, so following this guide isn't a problem for me, but I have some questions:
1. How risky is it to perform a BIOS upgrade? By the way I will upgrade the BIOS using Dell's "biosdisk" and "syslinux memdisk".
2. Does the BIOS upgrade through Ubuntu need a battery?
3. Is it fine to perform the upgrade from a live CD or I have to install Ubuntu on the HDD for that?

---

### Post by coldraven on 2013-11-16
> **eDFPxpX said:**
> My father's laptop is running Windows XP which is going to be unsupported in a matter of months. I want to upgrade the BIOS of the laptop as the current BIOS version can't run any newer Windows version. I know I can upgrade the BIOS using Windows but it requires a battery (ours is dead) to upgrade. 


But I found this guide to help me upgrade the BIOS: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)


I am a bit familiar with Linux command line interface, so following this guide isn't a problem for me, but I have some questions:
1. How risky is it to perform a BIOS upgrade? By the way I will upgrade the BIOS using Dell's "biosdisk" and "syslinux memdisk".
2. Does the BIOS upgrade through Ubuntu need a battery?
3. Is it fine to perform the upgrade from a live CD or I have to install Ubuntu on the HDD for that?

1. If you get a power cut or glitch then without the battery you will brick the laptop
2. I would guess that as you are going to use Dell's software it makes no difference whether it's run in Windows or an emulator
3. All the examples in your link are from people who have installed Ubuntu, it won't work from a Live CD because you need to reboot at some point and the DOS disc image will be lost.

Buy a new battery and backup the laptop before trying to update the BIOS.

---

### Post by mikewhatever on 2013-11-16
1. It's pretty risky, given that if something goes wrong, it can brick the machine. The BIOS disk sounds like a bad idea, in view of the following from the wiki you've linked to:
> NOTE that biosdisk hasn't been updated in almost a year and appears to be broken as of this writing (May 2012). See the "Updating the BIOS without without using biosdisk" section above for an alternative method.

biosdisk is a utility maintained by John Hull at Dell. There isn't an official Ubuntu package yet but the provided downloadable archive has an installer which can be used to upgrade your BIOS from Ubuntu. It also doesn't appear to work at all for Ubuntu. 
2. There is no such thing as a "BIOS upgrade through Ubuntu".  A more correct question would be - "Does Dell's BIOS disk require a battery?" or "Does BIOS update with FreeDOS require a battery". Good question. You are about to find out.
3. For What you've indicated, a proper installation of Ubuntu would be required. A Live CD is ok for testing, but whatever changes you make to the system will be gone after a reboot.

---

### Post by kevpan8152 on 2013-11-16
Upgrading the BIOS on a Dell system is a whole lot easier with Windows than without Windows. That said, one the the things Microsoft recently notified me about (due to the fact that I am a Microsoft Technet Subscriber) is that a 90 day Trial of Windows 7 Enterprise Edition will soon be posted on Microsoft's Technet Website free of charge!

---

### Post by mörgæs on 2013-11-18
You could try creating a bootable USB stick with Freedos and the new BIOS setup file. If it works it's a quick and easy task, and if it does not you will get an error message and you will not be worse off. 

I have upgraded many Dells, and it was always a smooth process.

---

### Post by blortuga on 2013-11-22
That 90-day trial sounds like a good idea.

I have tried creating a bootable USB stick with Freedos, and that did not work for my 7520 Inspiron.  The Bios updater exe just spit out an error under Freedos.

Fortunately (for me) - the successful method I found, was creating a bootable ISO using WinPE, but even that was not straightforward.  I had to use the Windows Deployment Kit to customize the WinPE image, and I had use the x64 image.  (the bios updater for my laptop would not run in 32-bit WinPE, either).  

The Windows Deployment Kit is free, but you can only run it (and consequently, build the bootable WinPE disk with the BIOS files) on Windows.  There may be a way for someone smarter than me (and more time on their hands) to figure out how to extract the necessary tools, and write them to a disk using Linux tools.

This complexity may have been an artifact of the weird configuration of my laptop. (it has EFI; so maybe that's why the bios updaters don't run in FreeDOS).  So this may not be the case for your laptop.

---

### Post by eDFPxpX on 2013-12-24
Oh no... I can't update as I don't have the battery. :( I used FreeDOS.
[IMG]http://i.imgur.com/dcjdU0f.jpg[/IMG]

---

### Post by eDFPxpX on 2013-12-27
Is there is any way I can perform a BIOS update without a battery?

---

### Post by mörgæs on 2013-12-27
Most likely not.
It's a safety feature. If the power cord is pulled out during a BIOS upgrade without battery backup the BIOS might go FUBAR.

---

### Post by eDFPxpX on 2013-12-27
> **mörgæs said:**
> Most likely not.
It's a safety feature. If the power cord is pulled out during a BIOS upgrade without battery backup the BIOS might go FUBAR.

Weird, I believe there must be an option to disable this for people who understand the risks of doing this. Buying a new battery for such an old laptop isn't worth it.

One more question (might be a stupid one :D ) : When I tried to upgrade the BIOS through Windows (when I had the dead battery), it refused to install the BIOS as battery isn't above 10%. If I found the battery and tried to repeat the upgrade, can FreeDOS know the battery's level if it is above or below 10%?

---

### Post by mörgæs on 2013-12-27
> **eDFPxpX said:**
> can FreeDOS know the battery's level if it is above or below 10%?

My guess is that BIOS senses the battery level and blocks the upgrade. 

Why not use the computer for Lubuntu? A 6400 is great hardware if you feed it a light operative system.

---

### Post by eDFPxpX on 2013-12-28
> **mörgæs said:**
> My guess is that BIOS senses the battery level and blocks the upgrade.

I thought about it the same way. :(

> **mörgæs said:**
> 
Why not use the computer for Lubuntu? A 6400 is great hardware if you feed it a light operative system.

If it was me who uses the laptop then I would do that for sure! But who uses it is my father, who doesn't like change at all. An upgrade to Vista or 7 is acceptable for him, but to something other than Windows, I don't think he will appreciate it (I even tried that before). :(

---

### Post by eDFPxpX on 2013-12-28
I just wanted to say to all of you thanks a lot for the help! :) I have successfully flashed the new BIOS without the need for a battery!

Basically that is what I have done:
1. Got a USB Drive and used [Unetbootin]("http://unetbootin.sourceforge.net/") to install FreeDOS on it.
2. Got the BIOS update file from [Dell Support]("http://www.dell.com/support/drivers/us/en/19") and Copied it to the root of that USB flash drive
3. Turned off the PC and booted into the USB flash drive. Sometimes you might need to change the BIOS settings to make it boot up from USB first, or maybe just go to the boot menu and choose to boot from USB.
4. **IMPORTANT:** Chose to run FreeDOS in **safe mode (without loading drivers)**.
5. FreeDOS started booting and when it finished it had A:\ as the drive it was viewing
6. Typed in "**C:\**" (without quotes) to open the root of the Flash drive.
7. Typed "**dir**" (without quotes) to see the file name of the .exe file to update the BIOS.
 8. Typed in the name of the .exe file with the parameter **/forceit **after the file name (**the filename may vary!**). This parameter forces the upgrade even if no battery was detected. In my case I believe that was "**MM061A17.exe /forceit**" (without quotes). **It is very important to leave a space between "filename.exe" and "/forceit"** otherwise it will not work! By the way I tried using the parameter "/forceit" on Windows without success, so better use FreeDOS.
9. Update started and completed successfully!

Sources:
1. This thread (Thank you all once again!). :D 
2. [http://ubuntuforums.org/archive/index.php/t-1901977.html](http://ubuntuforums.org/archive/index.php/t-1901977.html)
3. [http://club.myce.com/f7/how-update-bios-dell-laptops-without-battery-260714/](http://club.myce.com/f7/how-update-bios-dell-laptops-without-battery-260714/)

---

### Post by mörgæs on 2013-12-28
Good, please mark the thread 'solved'.

---

