---
title: "I lost my display on a new install of Ubuntu 11.10 - help needed"
date: 2012-03-13
forum: Desktop Environments
---

### Post by zheexh on 2012-03-13
Hello,

I'm new to ubuntu, as well as to linux. So please don't expect much general knowledge about things you might expect me to know and understand.

I've just installed ubuntu 11.10 on an older P4 box. The machine has an old video card (an nvidia Gforce Ti4400). The Live CD apparently auto-detected this card because the CD-loaded trial version of ubuntu (and also the installation session) were rendering the correct resolution for my flat screen monitor. It looked nice.

And that's what really puzzles me, because once the OS installation had completed and the system was rebooted, the graphics resolution came up very low (at 640X480) and when I clicked on 'displays' it showed "unknown" for the display type with 640X480 in the drop-down and no other options. If the OS on the CD was able to detect my display config, why wasn't the installed OS able to do it as well? That just seems strange to me. 

At that low res I couldn't see much of the desktop or much of any screens I was able to access.  And I had/have no idea how to find or change the display drivers. So I googled some of the symptoms and found someone with a similar issue was instructed to issue the following command:

```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Well, the situation seemed desperate so I tried that command and then rebooted. Now I can't even get a display at the login screen when I reboot the machine. I get a "no input" error on the screen instead. When I boot into recovery mode and select the root shell prompt and go to the /etc/X11 directory I can view xorg.conf with nano and I can see that it is in fact configured with nvidia settings. But I can't alter it or remove it because it tells me that it's a 'read-only file system'.  And sudo doesn't work from there plus the root password I set earlier doesn't work from a recovery mode session either (or at least I can't figure out how to make it work).

Since I can't get back to the desktop with a display signal and I can't figure out how to get any control via the recovery console, I decided that this forum must be the place to ask for help. I hope I'm right because I'm really stuck.

So can anyone please help me get my display back and get it set to the correct resolution for my display adapter? 

Thanks for reading.

---

### Post by zheexh on 2012-03-13
Update:

OK, I did the package repair option from recovery mode and after that it let me have read-write access to the file system for some reason. And, by the way, the first phase of the package repair session was full of failures that rapidly scrolled down the screen. It notified me that it would take several hours based on the packages it determined should be downloaded then reinstalled. But the operation finished in less than one minute. Obviously it failed. But I then had write capability from the root prompt, which I couldn't get before for unknown reasons. I'm not sure what happened, but I can manipulate and save the xorg.conf file now.

I had thought to keep the original xorg.conf file in the /etc directory before I executed the sudo nvidia-xconfig command earlier. I did it from a root terminal session that I managed to access from the desktop. I renamed the file with the 'mv' command to xorg.conf.hold and so I can  now rename it to xorg.conf and see if the system reboots with display again. I'm not doing it yet though because I'm afraid to lose write capability to the file system again, since I don't know what caused it before. Although I did find a post that claims I can remount the file system from the recovery console session as read-write if I issue:

```
# mount -w -o  remount  /
```So if it locks me out again, I might be OK. 

But what I really need to know is what to put in the xorg.conf file to get it to produce a higher resolution display. It has to be a 1.6 aspect ratio resolution (such as 1440x900). Can anyone tell me what I need to add to xorg.conf to achieve this?

Thanks

---

### Post by zheexh on 2012-03-14
I hate to keep replying to myself, but I keep learning of more apparent problems.

First, I have my display back and can now log in again. Changing the original xorg.conf file back to its name and the nvidia one to something else worked. But I'm still at 640x480 res. And I figured out how to get write access in the recovery session, plus I can access root from a terminal session as well when logged into the OS (although the window and characters are HUGE there).

I tried the package repair again to see if I could learn what the failures were. They are apparently DNS resolving errors for the mirror/archive server host names. After each of the long list of "Failed" items it shows things like "failed to fetch..." and "could not resolve..."  "us.archive.ubuntu.com" and "security.ubuntu.com" etc. 

So what's the deal with that? My internet connection is fine and there seemed to be no problems with any part of the several hours of downloads during the installation process. Plus I just checked and I'm able to resolve those hosts just fine. They both resolve to 91.189.92.* IPs.

It sure seems to be difficult to get this OS set up. I'm not sure why I'm having so much trouble. Although I thought the installation went smoothly, I fear the OS is somehow broken. I can't think of any other reason I'm having these problems. If it is broken I guess I don't know how to fix it.

Any thoughts from anyone?

---

### Post by Max Blyss on 2012-03-14
Sometimes you can get botched installs from an install disc that is burned at too high of a write - speed.

Don't know why, but it happened to me twice...  Now I burn all Linux install discs at the lowest possible write speed, and haven't had a recurrence of an issue that seems quite similar to yours.

It worked for me, and I hope it helps you.

---

### Post by zheexh on 2012-03-14
Thanks for the response, Max. It seems there's no obvious solution to my display issue or someone would have pointed me in the right direction by now.

I guess I'm not totally convinced (yet) that the install is borked, though. I in fact did burn the CD image at the slowest speed possible and it verified perfectly well. Plus there seem to be lots of people who have had trouble with nvidia vid cards and ubuntu display configuration. Except most of those instances seem to have been with v10.10 or earlier.

About the failed DNS resolve thing, I also tried *apt-get update --fix-missing* from both recovery mode and a terminal session within the OS. The recovery mode attempt generated those resolve failures, but the OS terminal attempt didn't. So I'm unsure what that means.

I just wish I could get the display to work at a higher, usable resolution. It's simply unusable at 640x480. If this is just a problem with the OS not supporting the video drivers then I sure don't understand why the CD version of the OS seemed to have no problems at all automatically setting up its much higher resolution on my system while the installed OS doesn't seem to be able to do that. Couldn't the developers have just made the OS do the same thing the CD image version does to produce the good resolution display?

---

### Post by zheexh on 2012-03-14
After a fair bit of experimentation (and some reading) I'm suspecting that the nvidia drivers aren't able to interrogate the monitor's EDID values, so they don't know what modes are available and thus the OS defaults to 640x480.

When I issue get-edid I see the following two lines within the return:

```
Monitor and video card combination does not support DDC1 transfers
Monitor and video card combination does not support DDC2 transfers

```and

```
The EDID data should not be trusted as the VBE call failed
```And in the Xorg.0.log file I'm seeing:

```
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.22.44
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4400 at PCI:1:0:0:
(--) NVIDIA(0):      CRT-1
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
Warning: Xrealloc: requesting unpleasantly large amount of memory: 0 bytes.
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):    "nvidia-auto-select".
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):      "nvidia-auto-select".
(II) NVIDIA(0): Virtual screen size determined to be 640x480
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0): from CRT-1's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) NVIDIA(0): Depth 24 pixmap format is 32 bpp
```So does anyone have an idea on how I can get this system to successfully query the EDID info from the monitor? To me at least, that seems to be what's wrong.

---

### Post by zheexh on 2012-03-14
It's hard to imagine that this would be such a difficult problem to address for everyone here. Not to sound harsh but honestly I'm about at wits end with ubuntu 11.10. Since no one seems to have any ideas for me, I decided to find (and try installing) some different display drivers for my Ti 4400.

At driversworld.us I found nvidia x86 Ti 4400 drivers that I thought might be worth a try. So downloaded and tried to install them. The system wouldn't let me install because X was running. So I went into recovery mode and tried there. I got a runlevel error so I tried switching to init 3 and discovered that the prompts for login and password in recovery mode after that wouldn't interpret my login and password as a login and a password. It would miss the first character typed for both of them and it printed my password in plain sight on the screen at the 'password:' prompt - usually with the first character cut off. Then when I hit return it would respond with "command not recognized" every time. So I began yelling out: "c'mon! it wasn't a command, it was a password!" And this behavior is entirely repeatable (and seemingly unavoidable).

Then when I tried to install the drivers without changing the runlevel and ignoring the warnings, the installer told me that if I'm running either the 2.4 or 2.6 kernel I need to be sure that the headers for the kernel match. The installation then failed. So I'm thinking that maybe those drivers are incompatible with the linux 3.0 kernel.

Actually, I had ubuntu 10.04 installed on the same computer up until about a week ago. I had installed it from a downloaded image about 2 years ago and it installed smoothly and ran well. I didn't use it very much while it was there because it's a dual-boot machine (with windows as well) and my linux experience is so slight.

And ubuntu 10.04 worked fine display-wise with the same exact hardware (Ti 4400 graphics card etc.) so I have to conclude that the developers messed up the newer ubuntu versions (in that regard at least).

I suppose I'm just frustrated but at this moment I think I should probably give up on ubuntu for now. It shouldn't be this difficult to get an OS up and running or to find viable answers for serious problems. I may have limited knowledge about linux systems and ubuntu but I'm surely not stupid and this has been a major headache and time consumer.

I tried at least. Sorry for writing a book about it. I'm just a bit upset.

---

