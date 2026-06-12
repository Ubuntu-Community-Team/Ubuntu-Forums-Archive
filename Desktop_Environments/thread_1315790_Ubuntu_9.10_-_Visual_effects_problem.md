---
title: "Ubuntu 9.10 - Visual effects problem"
date: 2009-11-05
forum: Desktop Environments
---

### Post by gabe17 on 2009-11-05
Hi, 

I am using Ubuntu 9.10. Everything is fine, but I have one small problem with it. When I try to allow Visual Effects, it searches for some drivers and then it writes that Dektop effects could not be enabled. 

Can somebody help me with my problem? 
Thanks.

---

### Post by 3Miro on 2009-11-05
Try going to System -> Admin -> Hardware and look for drivers from there.

What video card do you have?

---

### Post by gabe17 on 2009-11-05
I tried it...it found an ATI/AMD driver, but if I click "activate", it just shows "Downloading and installing driver..." window for a while and then it do nothing, the driver stays "not activated". My card is Asus Radeon HD3650. What should I do?

---

### Post by 3Miro on 2009-11-05
Hm, this should install and then ask you to reboot. I have no experience with ATI/AMD video, so I guess I cannot be of much help.

In any way, once you install the driver, you should be able to run the effects. Search for ATI/AMD driver issues (for your specific video card) and if you cannot find anything, start another tread asking about it.

---

### Post by gabe17 on 2009-11-05
Ok, I will try to start a new topic about the driver. Thanks for help.

---

### Post by jward3010 on 2009-11-05
I would suggest patience with the downloader. I thought it was fixed, but maybe not. It suffers from a bug where when it's downloading the driver the progress bar doesn't move, when it begins to install the driver you get a sudden jump to 80%. This lack of progress may seem to last for quite a while but something is happening and consider that these drivers can be anything from 50MB up to 120MB so they can take a while to download.

---

### Post by Pauly BC on 2009-11-05
+1 jward3010. 

When I installed the ATI driver for my 3850 it took a long long long long long long time and a reboot was required. You will know it was successful when you have ATI Catalyst added to the Applications menu.

Let us know once this is completed how smooth the desktop effects are. I found mine to be a little choppy.

p

---

### Post by gabe17 on 2009-11-06
At first, before this problem appeared, I had had the same problem as Pauly BC have (that the driver was installing very very long), but I simply thought that it will not install the driver and I ended this installation progress. Then I installed some drivers throught Synaptics package manager, and then appeared my actual problem (that window installing the driver appear only for few seconds and does nothing). 
So I will try to uninstall all drivers I've installed thru Synaptics and I'll do what Pauly BC did (I will wait a long long long time). ;)

---

### Post by jward3010 on 2009-11-06
Yeah, this is a silly bug. A progress bar should show progress in all stages of "doing something". The funny thing is that "Downloading packages" appears and it stays dead still so best thing to do then is look at your router and see if there's any network activity - if you're the only one online this will work, if not, then it's not a great idea.

Either way, the moral of the story is wait... wait more... and there you go.

---

### Post by Johnny M! on 2009-11-08
Howdy there gabe17

My ATI Radeon 4850 Card had the same (unresolved) issue.

I too, am frustrated by the upgrade to 9.10's inability to transfer the perfectly working graphics card setup and drivers from 9.04:
-----------------------------------------------------------------------------------------------------

 				 				**Help (if able)!: Upgrade to 9.10 Graphics Problem** 			
 			 			 		   		 		 		[B]Saturday 7-Nov-2009
-----------------------------

Second Posting of Topic - Please Help if you Can!
Thank you !!!!!!
---------------------------------------------------------------------

Serious Upgrade Problem (Ubuntu 9.04 to 9.10)[/B] 			
 			 			 		   		 		 		TGIF 6 Nov 2009
-------------------------

Hello Fellow Ubuntu Forumers,

Relatively new to Ubuntu; but have installed/used:

- 8.04 (Wubi)
- 8.10 (Clean Install - Dual Boot with GRUB to either Windows or Ubuntu)
- 9.04 (Upgrade from 8.10)
- 9.10 (Attempted Upgrade from 9.04) ????

My previous upgrade from 8.10 to 9.04 was painless and flawless. But my attempted upgrade from 9.04 to 9.10 had serious problems (ended up reverting back to 9.04 via Acronis True Image Home restoration).

Event Log:

- Attempted to Update 9.04 to 9.10 via Update Manager (29-Oct I think)
- Update appeared to go smoothly (but slow - I suffer from DSL)
- Booted into 9.10 and Desktop appeared normal; but I didn't have time to wring things out.
- A few days later, returned, booted up 9.10 and immediately ran Update Manager (maybe 20MB of stuff downloaded)
- Opened Firefox and was puzzled to see very strange Page Scrolling on web pages.
- Video was jerky and page extremely slow to scroll: almost like the video card was struggling to redraw the page as I scrolled down.
- So I first thought it was the new version of Firefox 3.5.4
- Then I noticed that all maximized window content scrolled the same way; regardless of application
- The jerky movement and slowness of page redraws rendered Ubuntu unusable!
- Smaller windows (sized 25% of my screen size) seemed to scroll OK?

- Troubleshooting:
- System / Administration / Hardware Drivers revealed that the system was NOT using my ATI proprietary Driver for my ATI Radeon 4850 Card (FGLRX); which was OK in previous Ubuntu build.
- 9.10 would not let me re-enable that video driver (FGLRX) in either Hardware Drivers or Synaptic Package Manager (even though it was present).
- I thought I could force the system to use the FGLRX driver so I removed the OS ATI video driver from Package Manager and rebooted.
- Still no Fix!
- Also discovered that the Screensaver functionality was totally inoperative!
- OK; at this point I gave up because I didn't want to devote the time required to fix this problem.  
- I reinstalled 9.04 (via Disaster Recovery Imaging Software)


There was NOT much online about my upgrade problem; except I did find this very interesting and made me feel that I may not be alone:

------------------------------------------------------------------------------------------------------------
[http://www.theregister.co.uk/2009/11...a_frustration/]("http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/")

Early adopters bloodied by Ubuntu's Karmic Koala

Ubuntu 9.10 is causing outrage and frustration, with early adopters wishing they'd stuck with previous versions of the Linux distro.

Blank and flickering screens, failure to recognize hard drives, defaulting to the old 2.6.28 Linux kernel, and failure to get encryption running are taking their toll, as early adopters turn to the web for answers and log fresh bug reports in Ubuntu forums.

The problems causing the biggest headaches are in graphics, with reports of flickering or dead screens. Adopters have re-downloaded and re-installed Ubuntu 9.10, and people have scoured the web for answers only to hit the same issues.

A bug has now being filed in Ubuntu forums on how Ubuntu 9.10 breaks graphics drivers and X, preventing log in or startx.

A conflict with graphics cards from Nvidia and ATI seems to be the issue, but there's no answer "why" or obvious fix.
--------------------------------------------------------------------------------------------------------------------------

My Plan:

- I'll wait a few weeks and attempt the Upgrade again
- Maybe I'll remove the ATI FGLRX Driver (use the OS version) before the Upgrade and then re-install it once the upgrade is complete. Good idea????

Any ADVICE / HELP Appreciated !!!!!!!!!

BVR
Johnny M!


PS: I also thought about a Clean Install of 9.10; but since I'm using GRUB to dual-boot, I'm afraid that Windows would be lost to the Master Boot Record (MBR); since the MBR points to GRUB (not Windows System partition root files: ntldr & Boot.ini) and I would wonder around in the wilderness of non-funtional computer.

C-Ya Later
):P

---

### Post by jward3010 on 2009-11-08
Sorry about your pain, sounds like it was a tough one for you. Some releases are great, some aren't and it depends on the level of hardware support for your particular machine. Stick with Jaunty for a while and maybe come back to Karmic in a few months, it might just be all great then.

---

### Post by gabe17 on 2009-11-16
I've solved my problem. I completely reinstalled my system (it wasn't big problem, because my instalation was clear, I hadn't have installed a lot of software on it). Then I tried to install the driver again, waited some time and it got installed. Some graffic effects are clear but some of them are a bit fiftul. Thanks everybody for help.

---

### Post by jward3010 on 2009-11-17
> **gabe17 said:**
> I've solved my problem. I completely reinstalled my system (it wasn't big problem, because my instalation was clear, I hadn't have installed a lot of software on it). Then I tried to install the driver again, waited some time and it got installed. Some graffic effects are clear but some of them are a bit fiftul. Thanks everybody for help.
What type of graphics card do you have (do you know)? Are you saying that some effects are slow and others fast or are some slow for a second or two and then improve?

---

### Post by Nadav34 on 2009-11-17
The default driver in the search for hardware drivers is one not to be played with. I have a Mac Pro with ATI Radeon 4870 HD and went to install those drivers only to have a fully destroyed system! WARNING: ALways try to find the correct video driver for your hardware, and stay far far away from the AMD/ATI driver bundled with ubuntu.

Because of it, I had to reboot and re-install as my xorg.conf and xserver were completely destroyed as well as for the fact that I couldn't even boot into console.

The link for the proper ati radeon driver 4800 series can be found here...

[http://www.amd.com/us/Pages/AMDHomePage.aspx](http://www.amd.com/us/Pages/AMDHomePage.aspx)

---

### Post by gabe17 on 2009-11-18
jward3010: My graphics card is Asus Radeon HD3650. Yes, for example when I start firefox, the effect of opening window stops in the middle for a second and then continues. I will try to make a screenshot of it. But the interesting thing is that other windows are opening clearly.
I hope my grafics card is good enough for ubuntu visual effects :)

---

### Post by jward3010 on 2009-11-18
The reason I say this is due to a hardware throttling system that some cards employ (nVidia's anyway - it's called PowerMizer). 

When very little is going on they slow down their core speeds to save power and heat but when you start something going they take around a second to accelerate back up to full speed, during that second you'll get slow performance but up to 30 seconds after that the card will work at full speed and you should find that all other actions are quick.

Then again I don't whether this is related to AMD/ATi cards. Definitely to lots of nVidia cards and not just laptop models.

---

### Post by hitman9211 on 2009-11-18
ALways try to find the correct video driver for your hardware, and stay far far away from the AMD/ATI driver bundled with ubuntu.:p

---

### Post by gabe17 on 2009-11-19
I found a driver on the ATI/AMD site. [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
Should uninstall the old one and install this one? Can you give me an advice how to uninstall the old? I wan't to avoid situation before a few weeks ago, when I uninstalled wrong driver packages in Synaptic and I couldn't log into the system.

---

### Post by jward3010 on 2009-11-20
I noticed easy enough install instructions on the same page in PDF format, just above the "Terms and Conditions" link.

---

### Post by gabe17 on 2009-11-24
So I tried to uninstall the old driver as it is written in the manual (/usr/share/ati, sudo sh ./fglrx-uninstall.sh), but it can't open ./fglrx-uninstall.sh. I checked whether there is this file, and it isn't. In usr/share/ati is only one folder with name "amdcccle".

---

### Post by gabe17 on 2009-11-27
So finally, I reinstalled the whole system (no just because of the driver, but I have had a bit more problems with it), installed the driver downloaded from the ATI/AMD site and now everything is fine, the effects looks much better than before. Thanks all for help and patience.  :)

---

### Post by noelvh on 2009-11-27
I know I used to use Envyng to install my video drivers!! Dose this still work? Its in the repos? I was lucky that with 9.10 I did not have to install any thing it just worked for me. I have an ATI x300 128mb on my laptop, and I have compiz running great.

Noel

---

