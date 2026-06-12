---
title: "Virtual box full screen"
date: 2010-01-14
forum: Desktop Environments
---

### Post by AmpersUK on 2010-01-14
PREAMBLE
Although I am not a games player as such, I am a serious poker player and have accounts on PokerStars, FullTilt and PKR.

These do not run well under Wine, so that, for the time being is out.

These do not run well under Adobe Flash in Karmic 9.10 so I do need to have Windows (7) running in a virtual machine. This works well and I have allotted two of my four gigbytes of RAM to it. However I have a 24" wide monitor and the virtual machine is too slamm to have both the game playing and the access page for other details I need. And also extra software to assess hand control.

I am contemplating buying a 64-bit computer with at least 12 Gigabyes of memory.

QUESTION ONE
How much of the 12 Gig of memory can I allot to the virtual machine and still have good performance for my other programs?

QUESTION TWO
How big a virtual Windows 7 window over my monitor will this give me?

Thanks in advance, I have also asked a few questions in a poll to see whether others are moving to 64-bit.

Ampers

---

### Post by 3Miro on 2010-01-14
I am doing scientific computing and that requires 64-bit (well it doesn't technically require, but the speed gain is significant enough o make 32-bit obsolete). I used to triple-boot windows XP for games, 32-bit Linux for regular use and 64-bit Linux for work. There used to be many issues with 64-bit Linux that made it hard to use for a primary OS. However, that is all in the past, with recent advances in wine and VirtualBox as well as 64-bit Linux, now I have only 64-bit Ubuntu 9.10 and I don't need anything else. They even closed the 64-bit forum, there is no need for a dedicated 64-bit forum anymore since the 64-bit issues are so few that they can be easily handled in the General forum.

- VirtualBox gives a warning if you try to assign more than half of your system RAM to the virtual machine, however, I have done 2GB RAM virtual machine on a 3GB RAM computer and it worked OK. With 12GB you should be able to do at least 6GB without problems, and my guess is more than that (trial and error will tell you when things get unstable).

- You can run VirtualBox in full screen mode and get just as much workspace as you would if you were using windows alone. You might have to increase the video RAM that you assign to the machine (24 inch is a nice big monitor). Currently VirtualBox doesn't allow more than 128MB video RAM for the guest, and that works fine on 512MB $50 Nvidia GF8600. In the future, VB would allow more video ram to be assigned to the virtual machine, so get a nice video card.

- If you plan to use 64-bit guest OS under VirtualBox, you will have to make sure you have the proper CPU that can handle the virtualization. Currently none of my 3 computers can support 64-bit guest OS (windows or Linux or anything). I am not exactly sure what you need, you might want to read up on that.

---

### Post by howefield on 2010-01-14
> **AmpersUK said:**
> QUESTION TWO
How big a virtual Windows 7 window over my monitor will this give me?

Not sure I understand "too slamm", but if you have guest additions installed, you should be able to go full screen on your monitor, in other words, the virtual machine can use all 24 inches of it if you wish.

---

### Post by AmpersUK on 2010-01-14
> **3Miro said:**
> 

- You can run VirtualBox in full screen mode and get just as much workspace as you would if you were using windows alone. You might have to increase the video RAM that you assign to the machine (24 inch is a nice big monitor). Currently VirtualBox doesn't allow more than 128MB video RAM for the guest, and that works fine on 512MB $50 Nvidia GF8600. In the future, VB would allow more video ram to be assigned to the virtual machine, so get a nice video card.

- If you plan to use 64-bit guest OS under VirtualBox, you will have to make sure you have the proper CPU that can handle the virtualization. Currently none of my 3 computers can support 64-bit guest OS (windows or Linux or anything). I am not exactly sure what you need, you might want to read up on that.

Thanks for that.

The video card I am getting is an nVidia Geforce GTS 250 - 1GB

My CPU will be an AMD Phenom II 940 Quad Core 3GHz with an 8MB cache

Not sure how to run VB in full screen mode, when I click the square (top right) I still only get the 8 square inches. But I will Google up on it.

How does Linux run with AM|D? I know Intel have a team of 700 Linux engineers on board, not sure about AMD.

Ampers

---

### Post by ChasHutch on 2010-01-14
Google "Virtual Box Guest Additions".  You will need to install it within Virtual Box.  This should solve your problem.

I think [this is the post]("http://www.mydigitallife.info/2009/11/25/how-to-install-virtualbox-guest-additions-in-linux-ubuntu-debian-fedora-opensuse-red-hat-and-more/") I used.

Also, my 64 bit Linux desktop uses an AMD triple core processor with 4GB and a nVidia GF8600 card.  I run XP in VirtualBox with Guest Additions (full screen) on one of my two monitors and an instance of turnkey linux (Wordpress).  The machine runs great and is on all the time.

Hope this helps.

---

### Post by 3Miro on 2010-01-14
If you have installed guest addons, the default to make VB runi n full screen is Right Ctrl + F, then Right Ctrl + F to exit. If this doesn't work, check to see which key is set up to be the "system" key. Virtual Box actually has e very good manual that you can get form VirtualBox.org, it is well divided into chapters and sections so you only need to read what you need and it is not very technical.

I use Athlon64 X2 on my Desktop for scientific computing, I have made this thing worked at 100% CPU usage on both cores for 2 weeks with only a few hours of rest here and there and it never even flinched. No problems or whatsoever, AMD has a great Linux support.

---

### Post by mkvnmtr on 2010-01-14
If I am understanding the second poster correctly the amount of video ram you allot may have something to do with the size you can get on the screen. I have always just accepted the default and some distros go full screen well and some do not. I rhink I am going to play with the video ram on a few of my systems and see if this is correct.

---

### Post by 3Miro on 2010-01-14
The default video RAM is about 16MB or something like that. Think about the largest resolution that you can get on a 16MB video card, it will not be much. With 16MB you should be able to do 1024x768 or maybe a bit higher, but who uses a monitor that small anymore. If you are to go full screen on a large monitor, go for more video RAM.

Technically 1024 x 768 = 786K dots, with about 4 bytes per dot = 3.5MB, go for double buffer to get smooth graphics and you have about 7MB of RAM taken just to support the resolution. This is with a very low resolution, the equation scales up quadratically with the size of the monitor (at my work the monitor would require at least 12MB and it is still only 17 inch) and the formula also ignores video hardware instructions and other overhead. Then every open window would ask for more video RAM and if the system runs out of video memory it will have to swap between main RAM and Video RAM which slows the system. Windows XP doesn't have effects, but any kind of windows 7 effect (i.e. transparency) would force that every window is stored in video RAM and this scaled the above more or less per window.

---

### Post by AmpersUK on 2010-01-14
[QUOTE=3Miro;8664190]If you have installed guest addons, the default to make VB runi n full screen is Right Ctrl + F, then Right Ctrl + F to exit. 

Thanks for that, I downloaded it, much easier, as someone said, in Windows on a Linux host.

*Right Control F* works perfectly, both ways, and *Right Control* by itself is no longer needed as the cursor is free flowing across the entire screen.

I have expanded the window so as not to cover my Linux window boxes (bottom right) so I can move between windows. The entire screen hid them with *RC F*.

So when the new 'pooter arrives, I can relax knowing I no longer have to dual boot.

**It would be useful if the VBox window with Windows in it could have access to the other drives on the computer.**

Does anyone know if this is possible?

Ampers

---

### Post by AmpersUK on 2010-01-14
> **mkvnmtr said:**
> If I am understanding the second poster correctly the amount of video ram you allot may have something to do with the size you can get on the screen. I have always just accepted the default and some distros go full screen well and some do not. I rhink I am going to play with the video ram on a few of my systems and see if this is correct.

I can't remember what I did. as I have 750mb I probably increased it to at least 250, but then I do have a fairly large monitor.

---

### Post by AmpersUK on 2010-01-14
I would like to thank the other contributors here as well. I am "tickled pink" that it all works perfectly, thanks guys.

---

### Post by akand074 on 2010-01-14
I have a 22 inch monitor and I ran XP fine with 32mb video and am running windows 7 now with 64 (I bet it would work with less). My resolution is 1680x1050 or something, your probably running at 1920x1080 or 1920x1200. if you are using 250mb that is far more than enough. If you have guest additions installed (click device then install guest additions at the top at the menu bar) it should run just fine. I personally like running in seamless mode (default hotkey Left Ctrl+L) now I just have my windows taskbar showing and everything else looks like ubuntu but I can run anything from windows just fine. You should be able to do the same.

In my opinion, 12GB of memory is unnecessary. You will never use it all. I only give 1GB of memory to my virtual machine and it runs just fine Ubuntu doesn't need too much. I would personally leave 2GB for ubuntu if your running a lot of stuff but even that. It was apparently tested that on windows vista there is no performance boost with more than 2GB of memory, after that its only for software that are RAM hogs. I'm currently building a computer and I'm not putting more than 4GB of memory, I just spend the extra money on higher quality RAM. 

Also it can not access drives, but with windows 7 you can access share folders or any homegroup folder. I guess you can make the entire drive a homegroup/share folder. 

Anyways I can ramble all day about stuff, I would make sure you have guest additions installed. Once its installed with the settings you already have it should run just fine at your full screen resolution I would think.

---

### Post by 3Miro on 2010-01-14
Read the manual for Guest Addons and Shared folders. Basically from Devices in the VB window you can assign a shared folder that would exist on Linux, but will be visible under Windows as "Network Drive". Thus you can share files between Windows and Linux.

---

### Post by AmpersUK on 2010-01-14
> **akand074 said:**
> In my opinion, 12GB of memory is unnecessary. 

Anyways I can ramble all day about stuff, I would make sure you have guest additions installed. Once its installed with the settings you already have it should run just fine at your full screen resolution I would think.

Yes, I am beginning to think I have the wrong end of the stick. However, as memory at oresent is so cheap, I will probably go for 8GB RAM if only to avoid swapping stuff repeatedly to disk.

I have Guest Additions installed and will take a look at the Manual and try to get my head around the shared folders concept.

Thanks

---

### Post by AmpersUK on 2010-01-14
> **3Miro said:**
> Read the manual for Guest Addons and Shared folders. Basically from Devices in the VB window you can assign a shared folder that would exist on Linux, but will be visible under Windows as "Network Drive". Thus you can share files between Windows and Linux.

Thanks, it is a complete partition I need to share but I am sure that will be taken as a "folder".

---

### Post by 3Miro on 2010-01-14
> **AmpersUK said:**
> Thanks, it is a complete partition I need to share but I am sure that will be taken as a "folder".

Every partition in a Unix or Unix like system (including Linux) is mounted (associated) with a folder. Technically, there should be no difference between sharing a partition and sharing a folder. The only issue may arise from permissions, i.e. who can write where.

I have a 4GB RAM Desktop and I never swap to HDD (only some of the most demanding scientific computation apps approach that number). Regular Web/Mail/Media even with Virtual Box, 4GB is enough. I can run VB (512MB) and a 3D game (Civilization) and several web-pager (youtube and flash included) and a music/video player at the same time and use no swap. If you do more than that, however, you may need more RAM. Also, RAM is cheap until you hit about 4GB, then it tends to get a lot more expensive, basically if 4GB cost X dollars, then 8GB would cost a lot more than 2X dollars, check with your vendor, it also depends where you live.

A feature in Linux is that the extra RAM doesn't get wasted. Linux uses the extra RAM to cash hard drive operations. Normally, this lets your system work more smoothly, then say windows (RAM cash is the main difference why windows XP under Virtual Box under Linux works faster/better than XP on it own), but the added benefit is negligible after some time. However, if you are going to move large files a lot or probably use Torrents or something along those lines, extra RAM can make significant difference.

---

### Post by AmpersUK on 2010-01-14
> **3Miro said:**
> A feature in Linux is that the extra RAM doesn't get wasted. Linux uses the extra RAM to cash hard drive operations. Normally, this lets your system work more smoothly, then say windows (RAM cash is the main difference why windows XP under Virtual Box under Linux works faster/better than XP on it own), but the added benefit is negligible after some time. However, if you are going to move large files a lot or probably use Torrents or something along those lines, extra RAM can make significant difference.

If I step up from 4gb to 8gb it is only an extra £50 if I choose the faster memory, so I will go for that. I may will want to run Kubuntu and maybe other flavours in the future, some of which I may want to run simultaneously.

If I have missed anyone, thanks for all your help.

---

