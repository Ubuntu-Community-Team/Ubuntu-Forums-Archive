---
title: "Dell Studio 1535 and Ubuntu"
date: 2008-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pah99 on 2008-10-06
This is just a post for those looking to buy a Dell Studio. I bought one and it works with Ubuntu. I have the following specs. 
Intel Core 2 Duo T9300 2.5GHz
4 GB DDR2 Ram
ATI Radeon Mobility 3450 256MB
Dell 1510 Mini N card (Broadcom Corporation BCM4322 802.11a/b/g/n)
Backlit keyboard
Ubuntu 8.10 Intrepid Ibex

All of these are correctly recognized by Ubuntu and work out of the box. If you are looking to buy this laptop, I highly recommend this laptop.

---

### Post by testbenchdude on 2008-10-08
I have nearly the same laptop, with a C2D t8100 and Dell wireless 1397 card; it came pre-loaded with Vista and was an absolute DOG even with 3gb of ram. I decided to try Ubuntu 8.04 LTS. I am comfortable with Windows and not so much with Linux but I've dabbled from time to time. Whether or not it works out of the box is highly conditional on just how you define "works".

Total time spent so far:

2 hours to be able play a DVD (still choppy, but at least I can play one)
4 hours to get the wireless driver installed and functioning
2 hours to get Flash to work properly within Firefox 3
1 hour to get BBC iPlayer to work properly within Firefox 3

I'll grant you, the install was effortless (and I had expected nothing less since first trying out Edgy Eft way back when) and the interface is slick. It is still a bit of a shock when I try to do things that seem so simple in Windows but don't work at all in Linux (I'm still flummoxed by the whole "permission" thing). In direct contrast, I was able to get, install, and configure the AMD drivers almost effortlessly which is a great testament to all of the development so far. I can forgive the ommision of the wireless drivers due to how new the hardware is, but the inability to watch DVDs and Flash without HOURS of in-depth terminal commands, more than half of which I still don't understand (copy paste is my dear friend!) is a deal-breaker for me.

Sure, it works. I was able to get online (via Ethernet) right after the install, which was a godsend since I had to rely on Google so much for the rest of it. But IMHO there's still a long way to go. Maybe I'll give it another go in another couple of years, but for now? Too frustrating, and god forbid one of my relatives installs this and then asks for my help (I have built and provided support for countless Windows boxes and networks over the years). I guess I'm not as much of a geek as I thought I was.

Now, can anyone tell me if I install Intrepid Ibex, will it do all of these things I have mentioned "out of the box"? If so, I woud be most willing to try it out.

Cheers~

---

### Post by patrickballeux on 2008-10-08
I would guess that you have an ATI card... Disable your Compiz effect and you'll get rid of the choppyness...


The problem is not Ubuntu, but the ATI driver.  Even with the latest driver (8.9) there are still issues.  Even in Windows, the ATI cards can be troublesome...

I currently have a DELL 1521, with the ATI x1200...  With Compiz disable, it works great...  DVD, Flash, games...

---

### Post by pah99 on 2008-10-08
I recommend you at least try out Ibex. Download the beta, and try it as a live CD. Can't hurt. As for the ATI card i have, it is recognized and I have proper resolution and stuff, but Ibex currently has a bug and so i can't install a real driver for it. So I can't say anything about the choppiness. Although I personally don't think that Compiz could be that much of a video card- hog.

---

### Post by Teamgeist on 2008-10-08
> **testbenchdude said:**
> 
2 hours to get Flash to work properly within Firefox 3

... and Flash without HOURS of in-depth terminal commands, more than half of which I still don't understand (copy paste is my dear friend!) is a deal-breaker for me.

FLASH is a matter of **seconds** by installing the ubuntu-restricted-extras package via the Synaptic Package Manager or by typing ```
sudo apt-get install ubuntu-restricted-extras
``` in a Terminal.

For DVD-Playback etc try **[www.medibuntu.org](www.medibuntu.org)** and follow the Repository instructions there. Very easy.

Remember this for the next time you install Ubuntu and it will save you a lot of time and frustration. :)

---

### Post by marioquark on 2008-10-11
i have the same pc and with ubuntu intrepid beta i can't hear audio from headphones jack out...
can you confirm this? have you solved this issue?

---

### Post by pah99 on 2008-10-12
I had the same problem, and I also have the solution. First off, let me just mention this. On Ubuntu, only one of the headphone jacks work (at least on my laptop). This is the one on the inside, between the mic and outside headphone jack. Maybe later on both will work, but for now, only one works. To get this jack to work do the following. In the top right corner is the volume control. Right click on this and go to open volume control. On the top you will see three tabs with the last one called switches. If you click on that you will see "Headphone as line out". Make sure that the box is checked. Now it should work. Here is the thing though. On my laptop, the last time I used the headphones, I had to manually mute the laptop speakers. For some reason Ubuntu doesn't realize that there are headphones plugged in and doesn't automatically mute the laptop speakers. Hope this helps.

---

### Post by marioquark on 2008-10-12
yes, i found the solution by myself some hours ago... a bit annoying procedure, but now it works.

i hope that official intrepid release will include a better intel hd driver. we'll see...

thanks a lot anyway.

---

### Post by netpro25 on 2008-10-26
If you enable the extra switches Analog Loopback's in preferences of Volume Control and check the first one it will disable the laptop speakers and then you can use external speakers without the internal ones. You would need to use this in conjunction with the Headphone as Line Out switch.

---

### Post by suncoolsu on 2008-10-27
Guys I also have a Dell Studio 1535 laptop with the following configuration.

Processor - Intel Core 2 Duo T8100
Video Card - Intergrated Intel(R) Graphics Media Accelerator X3100
BIOS Version - A04.

Initially when I installed ubuntu on this laptop I got the White Screen of Death. 

Then i changed the xorg.conf file - drivers to vesa in the Device section. This solved the WSoD problem but still I am not able to run ubuntu in "more aesthetically pleasing set of effects mode" (in Visual Effects). 

My laptop was able to handle an OS like Vista pretty well - So I think I should be able to enjoy Ubuntu with full visual pleasures. Currently it looks like a primitive machine with large icons which dont look very pleasing.

Also I dont think ubuntu recognizes my Video Card. I tried changing the xorg.conf file drivers to "intel" etc but to no avail. 

I am new to Linux (installed Linux as I hate Vista for its too slow and I needed Linux for my projects etc.)
Can someone tell me how to:
-make sure that my system detects the video card correctly
-how to install intel drivers (I know which drivers I should install) (using sudo apt-get install xserver-xorg-video-intel -- this didnt work)
-how to improve the visual pleasures of ubuntu enjoyed by me currently

Any help would be appreciated ...

B.

---

### Post by suncoolsu on 2008-10-27
To add if someone can asnwer these questions.

When I installed ubuntu. My Firefox worked pretty good - atleast I was able to watch videos on youtube and could listen songs at [www.pandora.com](www.pandora.com). I think during my struggle with the video drivers for X3100 i messed up something - and now I cannot see any video on the internet leave apart the case of listening to internet radio.

Can anyone help me with this problem as well? I tried installing firefox all over again :(

I am happy to say that ubuntu was able to detect ethernet and wifi without any problem :) ...

Thanks 
B.

---

### Post by darkadvice on 2008-10-31
> **suncoolsu said:**
> Guys I also have a Dell Studio 1535 laptop with the following configuration.

Processor - Intel Core 2 Duo T8100
Video Card - Intergrated Intel(R) Graphics Media Accelerator X3100
BIOS Version - A04.

Initially when I installed ubuntu on this laptop I got the White Screen of Death. 

Then i changed the xorg.conf file - drivers to vesa in the Device section. This solved the WSoD problem but still I am not able to run ubuntu in "more aesthetically pleasing set of effects mode" (in Visual Effects). 

My laptop was able to handle an OS like Vista pretty well - So I think I should be able to enjoy Ubuntu with full visual pleasures. Currently it looks like a primitive machine with large icons which dont look very pleasing.

Also I dont think ubuntu recognizes my Video Card. I tried changing the xorg.conf file drivers to "intel" etc but to no avail. 

I am new to Linux (installed Linux as I hate Vista for its too slow and I needed Linux for my projects etc.)
Can someone tell me how to:
-make sure that my system detects the video card correctly
-how to install intel drivers (I know which drivers I should install) (using sudo apt-get install xserver-xorg-video-intel -- this didnt work)
-how to improve the visual pleasures of ubuntu enjoyed by me currently

Any help would be appreciated ...

B.

Yea i'd like someone to look into this as well, i have the same problems and i know that it's an ubuntu related issue because Gentoo and Slack both operate fine graphically out of the box.

---

### Post by Ghuloomo on 2008-11-04
My friend she has the same laptop as well. Installed 8.4 and the WiFi didn't work. Upgraded it to 8.10 and everything worked fine, except when i watch videos the video blinks! i guess some problems with ATI driver ( i hate ATI )
Anyway, im trying to make a fresh install of 8.10 using my USB (i already put the iso and made it bootable using the System >> Administration >> Create a USB startup disk) but the problem is that I can't make the laptop boot from the USB.. I can't seem to get KingstoneTraveler as the first boot (though in every other BIOS system i could - I've used this usb to install on 2 other computers, excluding mine)

Can anyone solve this booting problem for me?

---

### Post by pah99 on 2008-11-04
Okay. This will be a reply to suncoolsu and darkadvice. I don't have the Intel video card (I have the ATI one), however I can offer you this advice. Have either of you tried to install ENVY? This is a program that figures out what drivers you need and will set them up for you. Try it out.

---

### Post by pah99 on 2008-11-04
Ghuloomo have you tried going into the bios (f2) and looking for some sort of USB booting option? I haven't seen one when I was in the bios, but there should be something in there. As for the flickering, its because of Compiz. Install the compiz fusion "switch" icon and set it to start up everytime you log on. It will appear in your notification area, and when you need to watch a video, just right click on it and go to "select window manager" and go back to metacity. When your done, just change back to Compiz. Its a pain in the butt, but you can only have one or the other, not both. Hope this helps.

---

### Post by robgolding63 on 2008-11-04
Has anyone managed to fix the headphone/speakers problem?

I have some speakers, but when I connect them to my Studio Laptop, the internal speakers don't mute - even if I check the first loopback (or any other combination I could think of!).

Just wondering if anyone has found a fix for it yet.

Rob

---

### Post by pah99 on 2008-11-04
To robgolding63. I still have the problem. The only way around (and easier than the switches thing) is to mute the front speakers, which is essentially the same as Analog Switch 1. 
I think the problem lies in the fact that there are volume controls for headphones AND front speakers. Thus, I think that because there are two thingys, then Ubuntu doesn't realise that headphones are plugged in or not. But thats just my take on things.

---

### Post by robgolding63 on 2008-11-04
Ok thanks. I'll try and find a way to script the muting/unmuting of the front speakers, so that I can just click a launcher and have it switch for me. That would be an acceptable hack until a fix or better driver is released.

Rob

---

### Post by pah99 on 2008-11-04
Hey thats a really good idea. Let us know how it goes.

---

### Post by suncoolsu on 2008-11-04
pah99 - Envy is only for ATI and NVIDIA Cards :( not for intel graphics card :(((

---

### Post by pah99 on 2008-11-04
Ah yes. You are absolutely right. Never even noticed it.

---

### Post by cjbarnes18 on 2008-11-04
I Just installed 8.10 on my Studio 1735 which is pretty much the same machine.

I am getting the same problem on the headphones, but the strange thing is it was fine on Hardy - all jacks working.

Does anyone know if this has been logged in Launchpad?

---

### Post by suncoolsu on 2008-11-04
Following is my configuration:
Processor - Intel Core 2 Duo (64 bit)
Chip Type - Mobile Intel 965 Express Chipset Family
VGA - Intel Graphics Media Accelerator X3100 (358 available memory)

Urs is the same?

I would be pleasantly surprised if it worked on ur config and not mine. I tired installing Fedora Core 9 - it also ended up with the same problem Ubuntu had. Atleast I was able to boot ubuntu in safe graphics mode at 800x600 resolution .. fedora core was just not happy with my 'poor' laptop ...

I think Linux has some grudge against me and my laptop :)

---

### Post by superm1 on 2008-11-07
Anyone encountering the "white screen of death", can you please try to upgrade to BIOS A05?

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R194079&SystemID=STUDIO1535&servicetag=&os=WLH&osl=en&deviceid=16523&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=268131](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R194079&SystemID=STUDIO1535&servicetag=&os=WLH&osl=en&deviceid=16523&devlib=0&typecnt=0&vercnt=3&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=268131)

You'll need to boot up a usb stick or cd drive with freedos or msdos to install it unfortunately at this point.

---

### Post by suncoolsu on 2008-11-08
nothing happened sir, I upgraded to A05 but still the same familiar WSoD

:confused: :( ](*,)](*,):?:

---

### Post by Kulgan on 2008-11-14
No white screen of death for me - that worked out of the box, and graphics and wireless (which fixed a sketchy connection problem) drivers installed fine from the proprietary driver installer. 

Remaining outstanding problems on this computer (for me):
 - Speaker issue (can't get it to work even after playing with the switches in teh volume manager) 
 - Manually altering screen brightness (ie Fn-UP/DOWN) causes an apparant loss of keyboard functionality (Ctrl-Alt-Backspace still work, though ^^) and an invisible mouse (which can't actually click). 

There also appears to be something sketchy with mounting partitions used by Ibex from Windows using the fs-driver, but I haven't done my homework properly on that one - there's probably a solution to all my troubles floating about there in the tubes.

---

### Post by superm1 on 2008-11-14
> **Kulgan said:**
> 
<snip>
 - Speaker issue (can't get it to work even after playing with the switches in teh volume manager) 
 
Also in intrepid proposed is an improvement to the audio mixer, but if you have no volume whatsoever, this may be a different problem.

> 
- Manually altering screen brightness (ie Fn-UP/DOWN) causes an apparant loss of keyboard functionality (Ctrl-Alt-Backspace still work, though ^^) and an invisible mouse (which can't actually click). 
<snip>

Fixed in intrepid proposed.  Activate intrepid proposed and grab the new kernel.
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721)

---

### Post by Kulgan on 2008-11-14
Thanks, will activate proposed immediately. 

I believe the sound issue was the same as previously mentioned, that the speakers were not muting no matter what combinations I used. I see my phrasing was rather ambiguous ;)

Thanks, will be updating in a little while! :D

---

### Post by pah99 on 2008-11-14
> **Ghuloomo said:**
> My friend she has the same laptop as well. Installed 8.4 and the WiFi didn't work. Upgraded it to 8.10 and everything worked fine, except when i watch videos the video blinks! i guess some problems with ATI driver ( i hate ATI )

Here is the solution for the blinking video (thanks to Kulgan).

Go to System-Preferences-Multimedia Systems Selector-Video-Default Output-Plugin. Change it form Autodetect to X Window System (No Xv). This will fix the problem.

---

### Post by Kulgan on 2008-11-14
So, got proposed up, and as far as I can tell I have the most recent builds available of the packages concerned available in the repos:

```

# apt-cache policy gnome-power-manager
gnome-power-manager:
  Installed: 2.24.0-0ubuntu8
  Candidate: 2.24.0-0ubuntu8
  Version table:
 *** 2.24.0-0ubuntu8 0
        500 http://no.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

# apt-cache policy linux-image
linux-image:
  Installed: (none)
  Candidate: 2.6.27.7.11
  Version table:
     2.6.27.7.11 0
        500 http://no.archive.ubuntu.com intrepid/main Packages

# uname -a
Linux studio 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```

LP bug says fix committed - guess I'll stick around that and wait for some nice updates to come my way. Gotta love the hardworking souls who make an effort for leechers like me ^^

As for the sound issue, is there anything that I may have to purge in case it interferes with an upgrade to the related packages? Would hate to figure out it was my playing around trying to get it to work that kept it broken...

---

### Post by pah99 on 2008-11-14
So I upgraded to the proposed linux image. The Fn key combos work correctly w/out messing everything up, but now I'm having issues with my sound. Now I can't mute my front speakers and listen to just my headphones. No matter what combinations of switches, nothing works. And this sucks a lot.

---

### Post by superm1 on 2008-11-14
The kernel you should be getting from proposed is linux-image-2.6.27-8-generic.  You are missing that.

---

### Post by pah99 on 2008-11-14
> **superm1 said:**
> The kernel you should be getting from proposed is linux-image-2.6.27-8-generic.  You are missing that.

No, that is the kernel that I installed. So it fixed the Fn button combinations from messing up the whole computer, but now the sound is messed up even more than with "image 7".

---

### Post by Kulgan on 2008-11-15
> **superm1 said:**
> The kernel you should be getting from proposed is linux-image-2.6.27-8-generic.  You are missing that.

Yup, now have the latest kernel, and the brightness keys work. Unfortuneately, the driver installer doesn't list wireless drivers yet, as it does for .27-7, so I'll have to find build them. No prob there.

Any progress on the sound issue anyone?

---

### Post by superm1 on 2008-11-15
> **Kulgan said:**
> Yup, now have the latest kernel, and the brightness keys work. Unfortuneately, the driver installer doesn't list wireless drivers yet, as it does for .27-7, so I'll have to find build them. No prob there.

Any progress on the sound issue anyone?
Install the matching linux-restricted-modules package from proposed and you'll get wireless

---

### Post by Kulgan on 2008-11-15
Amen. 
Keep it simple... that worked, of course.

What doesn't work is the ATI driver, though. It's listed in jockey, clicking Activate prompts for password and the "downloading and installing driver" progress bar flickers briefly, but doesn't appear to find anything, and nothing is installed. There is no error output when run from terminal, and output when trying to enable desktop effects is:
```

$ gnome-appearance-properties 
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

```

I'm assuming that the drivers should be enabled in Jockey first, so that makes sense, but it strikes me as odd that it lists the driver and is unwilling to install it.

---

### Post by superm1 on 2008-11-15
You need the 2.6.27-8 linux-headers too then...

---

### Post by Kulgan on 2008-11-15
Ok, I feel even more stupid now...
Stupid questions => simple answers. Thanks for spending your time on poor little sods like me :)

---

### Post by suncoolsu on 2008-11-17
I think u guys can also help me with installing the new release xf86-video-intel 2.5.0 of intel videosetting drivers(see at the bottom of this link - [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)) The readme file says that its the intel driver for the 965GM chipset. Since I am stuck with a 800x600 dispplay on my Dell Studio 1535 laptop (with 965 chipset and X3100 GMA) I have a strong feeling that it wud help me to improve the resolution ...


Thx

Pls help :(

B.

---

### Post by Kulgan on 2008-11-17
> Pls help :(
So.. What's the problem? Not compiling, settings problem, etc?

---

### Post by suncoolsu on 2008-11-18
please refer to my thread - unfortunately no one replied here

SOS

[http://ubuntuforums.org/showthread.php?t=973827&highlight=xf86-video-intel+2.5](http://ubuntuforums.org/showthread.php?t=973827&highlight=xf86-video-intel+2.5)

---

### Post by magdogg on 2008-11-18
Hi, also on a Dell studio with the brightness and headphone problems.

I have activated the intrepid proposed repository but I still dont get a linux-image-2.6.27-8-generic update option. The only thing related to this thread was a linux-restricted-modules common that didnt do much difference. 

Do I need to update something else in the proposed first to get access to the new kernel?

Cheers
/M

---

### Post by Kulgan on 2008-11-18
Did you actually go into Syaptic and look for it, or did you just keep an eye out for it in the update tool?

---

### Post by magdogg on 2008-11-18
Hi

Well I have checked in both synaptic and update manager. In synaptic those same updates (as in udm) are in the "upgradable" category. No new kernel in any case.

There is one update called linux-libc-dev which is described as "linux kernel heards for development".

No generic still though.

/M

---

### Post by superm1 on 2008-11-18
Search in synaptic for it

linux-image-2.6.27-8-generic

---

### Post by magdogg on 2008-11-18
Ahh thanks! There is was.

Is this safe to install by itself? And are there alot of other pkgs i need to install in order to complete the kernelupdate?

/M

---

### Post by superm1 on 2008-11-18
You'll need the accompanying headers and restricted modules

---

### Post by magdogg on 2008-11-18
Okay cool. So those are the only two packages needed except the generic one?

No meta package?

/M

---

### Post by superm1 on 2008-11-18
don't think there is a meta yet.

---

### Post by magdogg on 2008-11-18
Well I installed all those you suggested and so far so good!

The brightness Fn control works now (even though the visual indication is not there like in hardy).

Was there supposed to any change in the not getting sound in the headphones issue? Cause on my Studio 1535 there doesnt seem to be any difference. Still have to have headphones as line out switched in and manually mute the front when using headphones.

The overall volume though is much louder now.

/M

---

### Post by pah99 on 2008-12-03
So I have updated to 2.6.27-9-generic, and I'm back to square one with the sound and Fn key. Any ideas?

---

### Post by Kulgan on 2008-12-04
Enable Intrepid-proposed reposotories, install 2.6.27-10-generic. 

Now that both Fn-keys and the sound problem is fixed, smooth sailing ^^

Now for the IR remote with LIRC...

---

### Post by magdogg on 2008-12-04
Yea I also did that and was really disapointed, the -10 kernel in proposed fixed it though. And both my headphone jacks are working, whohoo.

Btw, does anyone know how the get the visual indication of brightness back? It worked on hardy!

/M

---

### Post by superm1 on 2008-12-04
> **magdogg said:**
> Yea I also did that and was really disapointed, the -10 kernel in proposed fixed it though. And both my headphone jacks are working, whohoo.

Btw, does anyone know how the get the visual indication of brightness back? It worked on hardy!

/M

A fix should be coming as soon as an archive admin ack's it into -proposed.
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/304187](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/304187)

---

### Post by magdogg on 2008-12-04
Ahh thats good news. What is/will the package be called?

/Cheers M

---

### Post by superm1 on 2008-12-04
> **magdogg said:**
> Ahh thats good news. What is/will the package be called?

/Cheers M
gnome-power-manager

---

### Post by Jammanuser on 2008-12-04
> **pah99 said:**
> This is just a post for those looking to buy a Dell Studio. I bought one and it works with Ubuntu. I have the following specs. 
Intel Core 2 Duo T9300 2.5GHz
3 GB DDR2 Ram
ATI Radeon Mobility 3450 256MB
Dell 1510 Mini N card (Broadcom Corporation BCM4322 802.11a/b/g/n)
Backlit keyboard
Ubuntu 8.10 Intrepid Ibex

All of these are correctly recognized by Ubuntu and work out of the box. If you are looking to buy this laptop, I highly recommend this laptop.

Yo! i have almost the **exact** same laptop! only mine is with the ATI Radeon HD Mobility 3400 series, also 256 MBs...oh, and i have 4GBs of memory, instead of 3! i also have the backlit keyboard, 320 GB hard drive, etc. ;)

Mine also works perfect with Ubuntu 8.10! :p

Cheers! ;)

-jammanuser

:D

---

### Post by solomoni on 2008-12-05
> **pah99 said:**
> This is just a post for those looking to buy a Dell Studio. I bought one and it works with Ubuntu. I have the following specs. 
Intel Core 2 Duo T9300 2.5GHz
3 GB DDR2 Ram
ATI Radeon Mobility 3450 256MB
Dell 1510 Mini N card (Broadcom Corporation BCM4322 802.11a/b/g/n)
Backlit keyboard
Ubuntu 8.10 Intrepid Ibex

All of these are correctly recognized by Ubuntu and work out of the box. If you are looking to buy this laptop, I highly recommend this laptop.
Hi suncoolsu, I have the same config. however came to me with Win Vista installed, I have downloaded the ubuntu studio-8.10-alternate-i386 and it does not work. Can you please help me on what & how to install it.

Cheers

---

### Post by pah99 on 2008-12-05
To Solomoni:
Have you considered trying the regular installer? I don't know much about the alternative, but last time I used it, it didn't go well.

---

### Post by pah99 on 2008-12-05
"

---

### Post by echo47 on 2009-04-21
My work just gave me a new Dell studio and I plan to install Jaunty on it in a few days.  Can anybody tell me if the trackpad and built in webcam/microphone are supported in this, or older versions?

---

### Post by Kulgan on 2009-04-21
I have a 1537 on which everything works with intrepid-proposed. Almost out of the box - the touchpad is fine, the camera and built-in mics work fine with Cheese and I imagine anything else that uses the v4l(2?) drivers. Jaunty should work fine, though I haven't followed the problems relating to ATI and the new X11, which were going to be solved before release. 

I'll be installing Jaunty this weekend. If you want to wait, I can tell you how it goes before you waste time potentially screwing over your comp. What Studio is it?

---

### Post by pah99 on 2009-04-21
> **echo47 said:**
> My work just gave me a new Dell studio and I plan to install Jaunty on it in a few days.  Can anybody tell me if the trackpad and built in webcam/microphone are supported in this, or older versions?

They do work! Although skype video is another story.

---

### Post by echo47 on 2009-04-21
It's a studio 1537, thanks for the offer but I think breaking the machine is part of the fun ;)  
As long as it's worked in the past I'm ready to give it a go, I just always wonder about laptops because the components can tend to be very propietary..

---

### Post by echo47 on 2009-04-27
I am on a studio 1537, and having trouble getting Jaunty to display in resolutions greater than 1280x1024 (the native resolution of the monitor is 1920x1200 and I've been able to get the Vista partition on this same machine to display to it properly).

I was wondering if anybody else has experienced this issue and resolved it.  I already tried upgrading libdrm-intel1.

Here is the output from lspci. 
```

jon@mabel:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```
I am planning to get an HDMI cord and try that connection also..
Is there anything else I can do that would be useful for troubleshooting?
Any help would be appreciated.

---

### Post by nagub on 2009-08-18
Hi echo47 , Kulgan 
    It seems , you already had some taste of installing Jaunty ( Dell ISO ) on studio 1537 .. 

I am planning  to upgrade/update my existing installation ( Jaunty 9.04 )   with the   Dell ISO that contains Jaunty along with Dell stuff..

Would you mind sharing your observations / notes , so that I will aware of those things.

Thanks in advance.

---

### Post by Kulgan on 2009-08-18
Haven't tried any Dell-specific CDs. 

However, most of Jaunty seems to be working fine, with exceptions including the IR receiver and lagginess when creating/unminimizing/resizing windows. There is apparently a solution to this here: [https://bugs.launchpad.net/bugs/351186](https://bugs.launchpad.net/bugs/351186) (which I have not installed yet because I am (almost) happy with the way things are. 

The (BIOS?) bug concerning the media keys that is present also in Windows carries over to Ubuntu, of course, but for me the solution has been to start the computer until GRUB shows, then pull battery out and start again. No problems after this manoeuvre. 

Go for it!

Cheers,
-K

---

### Post by nagub on 2009-08-18
BTW ,  [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)  is what I am referring to Dell ISO for Jaunty...

---

### Post by sarin_cv on 2009-10-15
I also have a Dell studio 1535... it didn't take more than 2 hours to install almost all the softwares I wanted. I was surprised to see my wifi working which I was not able to see with all other disros I have used. My bluetooth is also working perfectly. Webcam is also working with gYachi. Didn't test voice chat. I am pretty happy with ubuntu which I am using for the first time and hope this is my final distro hop. 

The applications I installed includes Thunderbird, Picasa, GTKam, AVIDemux, Bittorrent, Amarok, SMPlayer, Kaffiene, flash plugin, kopete, pidgin etc etc..... Almost everything I wanted...

---

