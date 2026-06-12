---
title: "lubuntu"
date: 2010-04-25
forum: Desktop Environments
---

### Post by tubunu on 2010-04-25
It's clear Lubuntu is going to get a lot of attention after its LTS release. However, I cannot find much information on it. I'd like to know: 

Will it run better on an old laptop that currently has Windows XP installed? In other words, I would like to know if Lubuntu will perform better or worse in terms of speed than Windows XP. (would anyone happen to know where to find a performance comparison chart of these two systems?)

Thanks!


**UPDATE: **
Here are the laptop specs:

HP Omnibook 6000
PIII, 700MHz, 192MB RAM

When playing videos (DVD) the picture tends to skip every now and then on Windows XP. It's kind of slow at times when performing every day tasks.

---

### Post by The Thunder Chimp on 2010-04-25
Not as good as a comparison chart, but I have heard that on lower end computers, Lubuntu and Xubuntu run faster and better than Windows XP on the same specs. Lubuntu (as compared to Ubuntu) can take downwards 128MB of RAM, Ubuntu needs 256MB of RAM. That's already a start, but LXDE and XFCE are lighter than GNOME (and Windows XP Luna).

---

### Post by kerry_s on 2010-04-25
> **tubunu said:**
> It's clear Lubuntu is going to get a lot of attention after its LTS release. However, I cannot find much information on it. I'd like to know: 

Will it run better on an old laptop that currently has Windows XP installed? In other words, I would like to know if Lubuntu will perform better or worse in terms of speed than Windows XP. (would anyone happen to know where to find a performance comparison chart of these two systems?)

Thanks!

what are the specs of the laptop?
yes, lubuntu should be lighter then all the other *buntu versions.
it's a custom lxde on the ubuntu base & has a very minimal selection of programs, you can use synaptic to install whatever else you want & tweak it to your liking.

i been using it since it went beta, only had minor problems with pcmanfm2 crashing, but it's still work in progress & crashes a lot less now, as long as i don't mess with the bookmarks it's fine.

---

### Post by FatalChaos on 2010-04-25
This should give you a bit more info about LXDE vs Gnome and KDE: 

[http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1)

---

### Post by snowpine on 2010-04-25
Windows XP is 9 years old and has lower hardware requirements than any version of *buntu. 

> The minimum hardware requirements for Windows XP Home Edition are:
Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
At least 64 megabytes (MB) of RAM (128 MB is recommended)
At least 1.5 gigabytes (GB) of available space on the hard disk

Also, XP is time-tested and very stable (when properly administered), while Lubuntu is betaware. I personally would not use Lubuntu until it has a stable release.

If you want meaningful advice from the forums, you should post your hardware specs. :)

---

### Post by The Thunder Chimp on 2010-04-25
> **snowpine said:**
> Windows XP is 9 years old and has lower hardware requirements than any version of *buntu. 



Also, XP is time-tested and very stable (when properly administered), while Lubuntu is betaware. I personally would not use Lubuntu until it has a stable release.

If you want meaningful advice from the forums, you should post your hardware specs. :)


Maybe, but regardless of software requirements, on a 128MB machine, Lubuntu and Xubuntu are faster than Windows XP. That's what I've heard, I don't have a 128MB machine, but Lubuntu is super fast.

---

### Post by snowpine on 2010-04-25
> **The Thunder Chimp said:**
> Maybe, but regardless of software requirements, on a 128MB machine, Lubuntu and Xubuntu are faster than Windows XP. That's what I've heard, I don't have a 128MB machine, but Lubuntu is super fast.

I do, and there is no way I would use Xubuntu on it (it's currently running AntiX). :)

I will hold off on giving advice until 1) we know the OP's hardware specs; 2) Lubuntu has a final release with official hardware requirements.

---

### Post by tubunu on 2010-04-25
First off, *thank you* to all who contributed to this thread. Here are the laptop specs: 

HP Omnibook 6000
PIII, 700MHz, 192MB RAM

When playing videos (DVD) the picture tends to skip every now and then on Windows XP. It's kind of slow at times when performing every day tasks. I wonder if Lubuntu would perform better?

---

### Post by snowpine on 2010-04-25
> **tubunu said:**
> First off, *thank you* to all who contributed to this thread. Here are the laptop specs: 

HP Omnibook 6000
PIII, 700MHz, 192MB RAM

When playing videos (DVD) the picture tends to skip every now and then on Windows XP. It's kind of slow at times when performing every day tasks. I wonder if Lubuntu would perform better?

Only one way to know for sure... burn a Live CD and give it a try. 192mb should be enough according to the Lubuntu Beta page.

I have a couple of old Pentium 3's and "kind of slow" is a good description.

(edit) ps there are much less drastic ways to prevent DVD skipping than reinstalling a different operating system, for example: 

> sluggish/jerky dvd playback

If your dvd playback is slow or jerky, add the cache and cache-min options to the command line like this:

mplayer -cache 8912 -cache-min 4 dvd://1

This means that you will have an 8MB cache, which should be plenty for a dvd. It will also fill the cache to 4% before starting, and the buffer should build up from there.

(source: [http://everydaylht.com/howtos/multimedia/mplayer/](http://everydaylht.com/howtos/multimedia/mplayer/))

---

### Post by kerry_s on 2010-04-25
> **tubunu said:**
> First off, *thank you* to all who contributed to this thread. Here are the laptop specs: 

HP Omnibook 6000
PIII, 700MHz, 192MB RAM

When playing videos (DVD) the picture tends to skip every now and then on Windows XP. It's kind of slow at times when performing every day tasks. I wonder if Lubuntu would perform better?


yeap, lubuntu would do well on that.
the video issues is a matter of getting the right settings for that machine. i use 
```
-nodouble -lavdopts skipframe=nonref:skiploopfilter=all

```in gnome-mplayer to play hd movies on my atom 1.6ghz smooth, same settings should work for you.

---

### Post by tubunu on 2010-04-25
Thanks!

I will download Lubuntu live CD once it hits gold and will update this thread with the results. In the mean time, feel free to add more here.

---

### Post by ibuclaw on 2010-04-25
If you are going to give Lubuntu a try, you might as well just switch to plain openbox as your Window Manager, you'll certainly get less overhead. :)

---

### Post by kerry_s on 2010-04-25
> **tubunu said:**
> Thanks!

I will download Lubuntu live CD once it hits gold and will update this thread with the results. In the mean time, feel free to add more here.

no need to wait, it's very usable.
[http://distrowatch.com/?newsid=06025](http://distrowatch.com/?newsid=06025)

the only thing that annoys me is the file manager, but it is perfectly fine for normal use. i have been trying other file managers cause i was bored & wanted to see how they get along in lxde, i had thunar+xfdesktop from xfce4 desktop, now i have nautilus from the gnome desktop.

---

### Post by him610 on 2010-04-25
Some of you had questions about the specifications of machines that one could install and run lubuntu; maybe this post will help. 
I downloaded lubuntu and attempted installation on several vintage machines, some successful, some unsuccessful.

A summary of the installation reports filed with the lubuntu development team follows:

Distro/Version
    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3

Computer Description:  
    * Dell Dimension XPS/D266 Pentium II  266MHz 128MBRam 
    * Installation process was unsatisfactory.
    
Computer Description: 
    * (Homebuilt) Tyan Mainboard, VIA VT8363/8365(KT133/KM133)(rev 02) AMD Athlon 850MHz 768MB
    * Installation process was satisfactory.
    
Computer Description:
    * eMachines T1115 Celeron 1GHz/100MHz 378MB (276MB used)
    * Installation process was satisfactory.
    Note: Also attempted installation with 256MB, but was unsuccessful.
    
Computer Description:
    * Dell Dimension 4400 Pentium 4   1.6GHz 1026MB (345MB used)
    * Installation process was satisfactory.
    
Computer Description:
    * Sony (Laptop) Vaio PCG-FXA36 AMD Athlon XP   600MHz 509MB (203MB used)
    * Installation process was satisfactory.
    
Conclusions:
lubuntu was intended to be installed on legacy hardware; however, there is a limit as to how far back one can go and expect a reasonable installation due to insufficient resources on older machines. 
The machines with insufficient rresources can be repurposed; the machine with the unsuccessful installation had been used as a fileserver running freeNAS for the last four years.
The lubuntu compares favorably with xubuntu with about the same hardware requirements. 

If anyone out there is interested in reading the full reports, I will gladly email a copy.
The information was collected using application, Hardinfo which gets installed with lubuntu.

Cheers,

---

### Post by kerry_s on 2010-04-25
> * Distro Version:	alpha3


is that a typo or did you go way back instead of using beta3? :lolflag:

---

### Post by Rodney9 on 2010-04-26
Lubuntu 10.4 Beta 3 goes brilliantly on new machines too, comes pae enabled , sees all my ram.

---

### Post by tubunu on 2010-04-26
> **hgh9mrp said:**
> 
Computer Description:  
    * Dell Dimension XPS/D266 Pentium II  266MHz 128MBRam 
    * Installation process was unsatisfactory.

Computer Description:
    * eMachines T1115 Celeron 1GHz/100MHz 378MB (276MB used)
    * Installation process was satisfactory.
    Note: Also attempted installation with 256MB, but was unsuccessful.
    
Oh, so I suppose having only 192MB of RAM might be a little too little..? :( I might go for an alternate CD or text installation.

> **hgh9mrp said:**
> 
If anyone out there is interested in reading the full reports, I will gladly email a copy.
The information was collected using application, Hardinfo which gets installed with lubuntu.
Cheers,

I would love to read the reports, if you don't mind posting them here so that maybe others would be able to read them as well. THANKS!

---

### Post by him610 on 2010-04-26
> is that a typo or did you go way back instead of using beta3? 

No, it wasn't a typo. I checked the dates of each report and they were all 13 or 14 March 2010. I have not found the time to work with any of the released beta versions yet.

---

### Post by him610 on 2010-04-26
> I would love to read the reports, if you don't mind posting them here so that maybe others would be able to read them as well. 

Okay, you asked for it. Be advised these reports are in the format requested by the development team and as I said before most of the information was collected from hardinfo.

**************/ Begin Installation Reports /********
InstallationReport-0
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  (Homebuilt) Tyan Thunderbird, VIA VT8363/8365(KT133/KM133)(rev 02)
    * CPU Type and Speed:  AMD Athlon 850MHz
    * RAM installed or specified to the kernel:  768MB
    * Hard disk type, capacity and partitions set up:  PATA Maxtor 90840D6 8GB SDA1=7.68GB SWAP=401584k
    * Video Card:  ATI Radeon R100 (Radeon 7200)
    * Display:  Acer AL1917
    * Networking:  Lite-On LNE100TX (rev 20)
    * Audio Hardware: SB Audigy 2 ZS (SB0350)
    
    Installation Procedure

I attempted to install directly from the CD, but it booted from the CD instead, and I wound up having to install from there using the "Install" icon. No error message was received when it failed to boot directly from the CD.
The speed of the installation process was satisfactory considering the age and limitations of the hardware.

1.  A notice of one broken piece of software popped up during the installaton process with the option of continuing the installation which I selected. I failed to take note of the defective software, and even though I have been using _buntu for over three years, I could not locate the installation logs. The installation process then continued to completion with no other problems encountered.

2.  In the configuration process when one is provided the opportunity to choose the user name and password, there is a checkbox to allow logon without a password which I checked. Subsequently, when logging on I still had to enter the password. Question: Does one still enter the password if one desires to logon without a password?
 
3.  After bootup, there was a noticeable flicker on the monitor. I selected Preferences->Monitor Settings; the Display Settings box appeared; it indicated VGA Monitor, Resolution 1280x1024, Refresh Rate 75. I selected Refresh Rate = 60 then clicked the OK button; the display momentarily goes to black then reappears with no flicker; however, there is no indication of the mouse pointer. My problem: how do I get out of the GUI with no mouse? After some trial and error, from a terminal window I use, "sudo /sbin/reboot" The system reboots; after logon I notice the flicker on the display is still present; checked the Display Settings again where the Refresh Rate is still set at 75. Evidently, the default rate is 75 which may be too high for some LCD monitors. I have read elsewhere that a Refresh Rate of 60 is a good setting for LCD monitors.

Summary

Installation process was satisfactory.
Broken software have also been encountered on other distro installations. 
Give some guidance as to where the installation or error logs are located.
The dialogue for password/no password option could be more clear.
The setting of the Display Refresh Rate needs to be addressed.
The disappearing Mouse Pointer needs to be addressed.

****************************************************
InstallationReport-1
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  Dell Dimension XPS/D266
    * CPU Type and Speed:  Pentium II  266MHz
    * RAM installed or specified to the kernel:  128MB
    * Hard disk type, capacity and partitions set up:  ATA Maxtor 86480D6  6GB 
    * Video Card:  Intel 82740 (i740)
    * Display:  Acer AL1917
    * Networking:  ADMtek NC100 10/100 (rev 11)
    * Audio Hardware: Onboard chip unknown
    
    Installation Procedure

I attempted to install directly from the CD, No install directly from the CD.

Errors:
  could not write bytes , broken pipe
  Disk error 01, AX =4200, drive 9F

Summary

Installation process was unsatisfactory. 
The demands of lubuntu lucid on this device is too much for the available resources on the described device.
I would also like to point out that there is a successful installation of Knoppix 2.6.28.4 on this same device.

****************************************************
InstallationReport-2
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  eMachines T1115
    * CPU Type and Speed:  Celeron   1GHz/100MHz
    * RAM installed or specified to the kernel:  378MB (276MB used)
    * Hard disk type, capacity and partitions set up:   ATA ST320410A 20GB SDA1=7.3GB/ext3 (Xubuntu 8.04), hda2=11.3GB/extended, SDA6=4.1GB/ext3, SDA7=6.3GB/ext3 (Lubuntu 10.4), SDA5=1GB/swap
    * Video Card:  Intel 82810E DC-133 CGC (rev 03)
    * Display:  Acer AL1917
    * Networking:  D-Link RTL8139 (rev 10)
    * Audio Hardware: ICH - intel 82801AA AC'97 (rev 02)
    
    Installation Procedure
Booted from CD. 
Began install process; chose side-by-side installation with Xubuntu 8.04.
The partitioning completed without problems followed by installation.

Errors:
Appeared while booting from CD, "could not write bytes , Broken pipe"
No other indications of errors observed.  

Summary

Installation process was satisfactory.

****************************************************
InstallationReport-3
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  Dell Dimension 4400
    * CPU Type and Speed:  Pentium 4   1.6GHz
    * RAM installed or specified to the kernel:  1026MB (345 used)
    * Hard disk type, capacity and partitions set up:  ATA Hitachi HDS72168 80GB /sdb1 /sdb1/swap
    * Video Card:  nVidia NV11 [GeForce2 MX/MX 400] (rev b2)
    * Display:  Acer AL1917
    * Networking:  Davicom 21x4x DEC-Tulip compat 10/100 (rev 31), Broadcom BCM 4306 802.11b/g (rev 02)
    * Audio Hardware: Intel 82801BA/BAM (rev 05)
    
    Installation Procedure
Booted from CD.
Entered required information.
Choose partitioning scheme.
System installed with no problems.

Errors:
No indication of errors encountered.
BCM4306 not configured during installation and setup.
Unable to activate B43legacy wireless driver - Dialog Box reports, " You are not authorized to perform this action."

Summary:

Installation process was satisfactory. 
This is the first time I have every had a problem activating a hardware driver.

****************************************************
InstallationReport-5
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-14
    * Distro Version:	alpha3
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  Sony Vaio PCG-FXA36
    * CPU Type and Speed:  AMD Athlon XP   600MHz
    * RAM installed or specified to the kernel:  509MB (203MB used)
    * Hard disk type, capacity and partitions set up:   ATA IC25N060ATMR04-0 60GB, sda1=fat32/30MB, hda5=fat32/9MB, sda6=ext4/7MB with Lubuntu-Lucid, sda7=free/8GB, sda8=ext3/5MB with Xubuntu-Karmic, hda9=swap/1GB 
    * Video Card:  ATI Rage Mobility P/M AGP 2x (rev 64)
    * Display:  unknown 1024x768
    * Networking:  Realtek RTL8139/8139C/8139C+ (rev 10)
    * Audio Hardware: VIA686A - VIA 82C686A/B rev50
    
    Installation Procedure
Booted from CD. 
Installed without problems.

Errors:
Appeared while booting from CD, "could not write bytes , Broken pipe"

Summary
Installation process was satisfactory. 

****************************************************
InstallationReport-6
Distro/Version

    * Distro Installed: lubuntu-lucid-i386  2.6.32-16
    * Distro Version:	beta1
    * Installation method: CD

Computer Description

    * Computer Manufacturer, Model Name:  eMachines T1115
    * CPU Type and Speed:  Celeron   1GHz/100MHz
    * RAM installed or specified to the kernel:  378MB 
    * Hard disk type, capacity and partitions set up:   ATA ST320410A 20GB SDA1, swap
    * Video Card:  Intel 82810E DC-133 CGC (rev 03)
    * Display:  Acer AL1917
    * Networking:  D-Link RTL8139 (rev 10)
    * Audio Hardware: ICH - intel 82801AA AC'97 (rev 02)
    
    Installation Procedure
Booted from CD. 
Began install process; chose whole disk installation
The partitioning completed without problems followed by installation.
Installation was successful even though CD Inspection had indicated error in one file. 

Errors:
Splash Screen choices:
CD Inspection indicated there was one file on the CD with an error.
Install from CD also inspects files on CD; results indicated one file on CD with error; process would not continue with installation.
Initially thought I may have burned a defective CD; however, I burned another CD and got the same error indication on one file after the CD Inspection.
No other indications of errors observed.  

Summary
MD5SUM of lubuntu-lucid-beta1.iso check was good.
The options on the Splash Screen worked with this release including CD Inspection
Installation process was satisfactory. 

**********/ End Installation Reports /************* 

As I was entering the information from the various reports, I noticed that I did make a couple of installations with the beta1 release.

---

### Post by tubunu on 2010-05-01
Thanks!

---

### Post by johnny2m on 2010-05-05
> **tubunu said:**
> 
Here are the laptop specs:

HP Omnibook 6000
PIII, 700MHz, 192MB RAM

When playing videos (DVD) the picture tends to skip every now and then on Windows XP. It's kind of slow at times when performing every day tasks.

Hey, I have the same laptop, with the same RAM, but 650MHz processor.

I'm currently using [u-lite]("http://u-lite.org/") (formerly ubuntulite), which is another ubuntu-based distro that uses LXDE, and it's been pretty good.  I've tried numerous other distros on it in the past, and I would say Xubuntu would be too heavy.  I've not tried Lunbuntu yet, but intend to in the next couple of weeks.

This article compares resources of L/X/Ubuntu:

[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

Might be a bit out-of-date, but shows Lubuntu is pretty light, and Xubuntu is not that light at all!

If you've got a couple of days to spare, try this thread for other light distro ideas:

[http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)

---

