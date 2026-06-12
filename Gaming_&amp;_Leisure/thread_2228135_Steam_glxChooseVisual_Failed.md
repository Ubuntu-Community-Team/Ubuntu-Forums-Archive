---
title: "Steam: glxChooseVisual Failed"
date: 2014-06-05
forum: Gaming &amp; Leisure
---

### Post by Bubblegut on 2014-06-05
I installed steam a week ago and it loaded up just fine but, I did not have an account yet so I had not actually started steam. A few days ago I made an account and decided to start steam again. What happens now when I start steam is it gives me an "Updating Steam" screen then that closes and a little pop-up says "glxChooseVisual Failed". I do not know what my video card is and I actually have little experience with Linux Ubuntu. When I ran steam in terminal I got this:

```
id@iD-RaffleBox:~$ steam &
[1] 4010
id@iD-RaffleBox:~$ Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1401381906_client)
Installing breakpad exception handler for appid(steam)/version(1401381906_client)
Installing breakpad exception handler for appid(steam)/version(1401381906_client)
Installing breakpad exception handler for appid(steam)/version(1401381906_client)
[0605/210636:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153
Serial number of failed request:  38
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153
Serial number of failed request:  39
xerror_handler: X failed, continuing
Steam: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  153
Serial number of failed request:  40
xerror_handler: X failed, continuing
glXChooseVisual failedAssert( Assertion Failed: Fatal Error: glXChooseVisual failed ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/Main.cpp:285


Installing breakpad exception handler for appid(steam)/version(1401381906_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20140605210636_6.dmp
id@iD-RaffleBox:~$ Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-39ca1f32-b028-4f0f-8824-84e2d2140605

```
Any help?

---

### Post by deadflowr on 2014-06-05
Thread moved to Gaming and Leisure

---

### Post by oldrocker99 on 2014-06-06
OK, to start with, enter this:

```
lspci
```

You want to look for the line which has "VGA" in it, which should tell you your graphics card or chip. If it's ATI, you probably have only open soource drivers available, **unless** it's a new enough card that the ATI fglrx drivers can be installed. Installing them on ATI "legacy" chips or cards will break your system.

---

### Post by Bubblegut on 2014-06-06
I did that and got this: 

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4550]

---

### Post by oldrocker99 on 2014-06-06
Your video is supported by the ATI proprietary drivers, which you can install using Hardware Drivers, and let it look for your hardware and drivers available. It **should** recommend a driver, which you allow it to install, and then reboot. The Catalyst Control Center should be available to you. Note that this is indeed considered a "legacy" chip by ATI and the newest Linux driver is from 1/2013.

I am an nVidia user; does anyone know whether this user would have better results with the current open source driver?

---

### Post by Bubblegut on 2014-06-06
Okay, sounds like a fix but I'm having a new problem.
I assume that Hardware Drivers is somewhere in my computer so I went to Dash and searched for it. I got an app called AMD Catalyst Control Center. When I click on it, it says I have no AMD graphics driver or it's not functioning properly. So, I did some searching and found what I think to be the correct driver for my computer:
[AMD Catalyst&#8482; 13.1 Proprietary Linux x86 Display Driver]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip")
When I download it however, I cannot seem to get the installer to run. How do you run the installer from terminal (exact code)?  Sorry for the hand holding but I'm just starting out.

---

### Post by oldrocker99 on 2014-06-07
To install the ATI Catalyst drivers, refer to this thread, ignoring the nVidia specifics:[http://ubuntuforums.org/showthread.php?t=2227232](http://ubuntuforums.org/showthread.php?t=2227232).

You need to skip down to the **INSTALLING NVIDIA DRIVERS** section and simply substitute the name of your ATI driver for the nVidia driver.

---

### Post by Bubblegut on 2014-06-08
Thanks! I'm hoping I am able to install the driver with that method as I had trouble with doing it in console. I am now presented with this problem:
[Cannot Login to TTY]("http://ubuntuforums.org/showthread.php?t=2228621&p=13044615#post13044615")
When I get that issue resolved I will come back to this thread and continue with the driver installation.

EDIT:

I can login to my tty, if the Nvidia guide works, I'll be sure to update!

---

### Post by Bubblegut on 2014-06-08
Only issue now is when I install the driver for my system it tells me that it is not the right one. I looked up the specific driver for my machine when I downloaded it but it does not seem to be the correct one.

---

### Post by Bubblegut on 2014-06-09
Issue Resloved.
TL;DR I installed the amd driver for my system then installed Bumblebee. A big thanks to oldrocker for his help in getting me as far as I did.

---

### Post by oldrocker99 on 2014-06-09
Great! It's considered good forum etiquette to mark a resolved problem as {SOLVED], by the way.

---

### Post by oldrocker99 on 2014-06-09
Great! Sorry you had so much trouble; it reminds me of my first days using 8.04!

---

