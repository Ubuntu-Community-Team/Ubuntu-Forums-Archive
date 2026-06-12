---
title: "Vostro 1400"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by aldenhg on 2007-08-01
I've just ordered a Dell Vostro 1400 with the 2ghz/800mhz/4mb Core 2 Duo, the normal screen, the 8400M GS, 2 gb of ram and (somewhat regretfully) the Dell wireless. I have a few questions for anyone who has a similar setup. 
First, how is the wireless? Does it work out-of-box and if not how about with ndiswrapper?
Second, do you virtualize Xp/Vista? If so, which VM do you use and what kind of performance do you get? I know that the C2D can do some amazing things when it comes to virtualization and I'd like to take advantage of it.
Third, do suspend/hibernate work? 
Fourth, how is the battery life? I ordered the longer life battery and I 'm hoping that it will be something north of 4 hours of intermittent use. 
Fifth, how is the 8400M GS? Which drivers do you use for it and how is the performance? I'm really most concerned with Compiz Fusion. I've gotten rather used to the eyecandy on my desktop and I'd like to take it with me.
Lastly, what have your general impressions of the machine been? I never think to ask these questions before I buy, but they were having a really good deal on the 1400: 2gb/120gb standard. It was a little tough to pass up.

UPDATE:
I followed most of chadteck's instructions and using the piix module my DVD drive works. I've stuck with the 2.6.20-15 kernel because the ethernet and wireless wouldn't work for me under the -16 kernel. As for the wifi, I'm using ndiswrapper with the windows driver and it works pretty well, but I'm kind disappointed that I can't use kismet with it. As for sound, I just searched the forums for "1420 sound" and followed the directions that popped up, It would appear that the Vostro 1400 and the Inspiron 14420 share an awful lot of hardware and therefore How Tos for the two are more or less interchangeable, as long as you make sure that you bought similar options (wireless, video card, etc.). I ended up spending about about 5 hours when I first got the computer getting everything working and I'm still not 100% there. Suspend and Hibernate don't work yet, but I'm working on it. I'll u[date more if/when I get it working.

---

### Post by kamaboko on 2007-08-01
The Vostro is a brand new line.  Very few people have them, so don't expect answers soon.  I've got one coming around the 13th.

---

### Post by aldenhg on 2007-08-02
That's about when mine should arrive. Good luck!

---

### Post by chadteck on 2007-08-03
> **aldenhg said:**
> I've just ordered a Dell Vostro 1400 with the 2ghz/800mhz/4mb Core 2 Duo, the normal screen, the 8400M GS, 2 gb of ram and (somewhat regretfully) the Dell wireless. I have a few questions for anyone who has a similar setup. 
First, how is the wireless? Does it work out-of-box and if not how about with ndiswrapper?
Second, do you virtualize Xp/Vista? If so, which VM do you use and what kind of performance do you get? I know that the C2D can do some amazing things when it comes to virtualization and I'd like to take advantage of it.
Third, do suspend/hibernate work? 
Fourth, how is the battery life? I ordered the longer life battery and I 'm hoping that it will be something north of 4 hours of intermittent use. 
Fifth, how is the 8400M GS? Which drivers do you use for it and how is the performance? I'm really most concerned with Compiz Fusion. I've gotten rather used to the eyecandy on my desktop and I'd like to take it with me.
Lastly, what have your general impressions of the machine been? I never think to ask these questions before I buy, but they were having a really good deal on the 1400: 2gb/120gb standard. It was a little tough to pass up.

1.  I've got the Intel 4965 Wireless card.  It was far from working out of the box, but I've got it working.  I'm not sure about the Dell wireless, but I read that the Intel Wireless G worked out of the box.

2.  Not yet, but I am using VMWare on my desktop to do this, and the performance is very good. At least as good as the Windows version of VMWare.

3. Good question. I haven't noticed.  I would try it but I'm not at home.  Other power management related things appeared to be working alright, so there is a good chance.

4. As with any laptop, it will vary depending on what you do, but I'd say that you could probably pull off 4 hours with the 9 cell with light usage.  I haven't actually timed it though.

5. The card is pretty nice for a laptop card.  I installed Compiz Fusion with no problems after I had the video driver installed (I manually installed the one from Nvidia's website.  As far as I know, there is one available for the 8xxx series in the official Ubuntu repo).  There seems to be a delay sometimes when the card is doing 3d operations off and on.  I haven't looked into this too much, but I have a feeling it has something to do with speedstep and/or Nvidia's power saving technology.  I think that using Compiz while on the battery is going to prove to be quite a drain, and I wouldn't expect to run from the battery for nearly as long while using it.

6.  It isn't perfect, but I like it.  Check out [this thread]("http://forums.slickdeals.net/showpost.php?p=7479562&postcount=983")on another forum that I frequent.  The link is actually a mini-guide I posted to help get everything working.  Iif you look at the rest of the thread, you should find everything you want to know about the laptop.

---

### Post by daveyiv on 2007-08-03
> **chadteck said:**
> 1.  I've got the Intel 4965 Wireless card.  It was far from working out of the box, but I've got it working.  I'm not sure about the Dell wireless, but I read that the Intel Wireless G worked out of the box.

2.  Not yet, but I am using VMWare on my desktop to do this, and the performance is very good. At least as good as the Windows version of VMWare.

3. Good question. I haven't noticed.  I would try it but I'm not at home.  Other power management related things appeared to be working alright, so there is a good chance.

4. As with any laptop, it will vary depending on what you do, but I'd say that you could probably pull off 4 hours with the 9 cell with light usage.  I haven't actually timed it though.

5. The card is pretty nice for a laptop card.  I installed Compiz Fusion with no problems after I had the video driver installed (I manually installed the one from Nvidia's website.  As far as I know, there is one available for the 8xxx series in the official Ubuntu repo).  There seems to be a delay sometimes when the card is doing 3d operations off and on.  I haven't looked into this too much, but I have a feeling it has something to do with speedstep and/or Nvidia's power saving technology.  I think that using Compiz while on the battery is going to prove to be quite a drain, and I wouldn't expect to run from the battery for nearly as long while using it.

6.  It isn't perfect, but I like it.  Check out [this thread]("http://forums.slickdeals.net/showpost.php?p=7479562&postcount=983")on another forum that I frequent.  The link is actually a mini-guide I posted to help get everything working.  Iif you look at the rest of the thread, you should find everything you want to know about the laptop.

Deja vu lol. Did you happen to get your ethernet working? I still can't seem to figure that one out.

---

### Post by kamaboko on 2007-08-03
I just got a shipping notification on  my 1400.  I'll keep ya'll posted on how it cooperates with Ubuntu.   My Compaq lappy was great at first but then Ubuntu started falling apart.  Too many issues to post at this moment.

---

### Post by chadteck on 2007-08-03
> **daveyiv said:**
> Deja vu lol. Did you happen to get your ethernet working? I still can't seem to figure that one out.

Yeah.  Bascially, I upgraded the kernel to get my wireless driver working, and the onboard ethernet was working fine with the new kernel. 

Edit:  You can either follow the below instructions if you feel like upgrading your kernel, or you can try the method that Dell actually uses to get it to work:

1.  Install DKMS from [http://linux.dell.com/dkms/dkms.html]("http://linux.dell.com/dkms/dkms.html")

2.  Get the package for the network card fix from [this post]("http://ubuntuforums.org/showpost.php?p=3117500&postcount=49") it is in the "main" package, but you might find some of the others useful.

I haven't tried this method since I upgraded my kernel, but I don't see why it wouldn't work.

/Edit  

Original instructions for upgrading kernel if you don't want to use the method above.

You will have to re-install the Nvidia driver at the very least, and your DVD-ROM will stop working.  The piix module has been removed from this kernel and ata_piix is the replacement; it requires a patch to work properly with the Vostro 1400.  If you decide to go forward with this, I can post the info regarding getting the patch applied and re-building the ata_piix module.

 I'll just post the first part of the wifi guide I used which has the instructions for getting the Gutsy kernel:

1. add a reference to the gutsy sources for the installation of the 2.6.22-9-generic kernel.
(I'm told the most recent kernel is changing frequently; look for the most recent kernel and substitute
any references within the guide to 2.6.22-9-generic with that most recent you are using)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

(graphically the above can be added via system->administation->sources add the line exactly as it is)

or alternatively via the terminal, copy and paste the above sources into the following file.

sudo gedit /etc/apt/sources.list


2 install the following; (kernel and sources), after having updated the sources.
(substitute '2.6.22-9-generic' with the most recent kernel)

linux-image-2.6.22-9-generic
linux-headers-2.6.22-9-generic

REMOVE THE CHANGES TO THE SOURCES MADE IN STEP 1, unless you want the unstable gutsy package updates (which I do not advise)

---

### Post by kteoh on 2007-08-04
The components are roughly the same as the Inspiron 1x20 series, so it's likely that if someone else gets it working, you can follow the steps closely.

Has anyone gotten it to work on 64-bit alternate?

---

### Post by aldenhg on 2007-08-04
Has anyone tried the Windows driver with ndiswrapper before going for the updated kernel? I'm kinda hoping to go with a more-vanilla-than-not Ubuntu installation and running a dev kernel with a custom compiled piix module isn't exactly that. Either way, my 1400 shipped yesterday and should be here by the end of next week. I'm practically wetting myself with anticipation.

Oh, also, have you tried suspend/hibernate yet?

---

### Post by PeggySue on 2007-08-07
I have a Vostro 1000  with AMD Athlon 64 X2 and the 1390 wireless mini card.  This morning I shrunk the vista partition using the vista disk manager, installed Ubuntu 7.04 (AMD 64bit version) and followed this link to install the wireless driver: [http://ubuntuforums.org/showthread.php?t=297092&highlight=wireless+network ]("http://http://ubuntuforums.org/showthread.php?t=297092&highlight=wireless+network")

The wireless network came up first time is is working with no issues so far.

Hibernate and suspend seem to do something sensible but I need to play some more to be sure.

---

### Post by cb951303 on 2007-08-07
some of the dell wireless cards works with oss broadcom drivers. 
you had the option of intel 3945 wireless  though, which works out-of-the box...

---

### Post by PeggySue on 2007-08-07
The Dell Vostro 1000 has options for 1390, 1490 and 1505 wireless cards.  I chose the cheapest!!  If I had known that the Intel 3945 card worked out the box I would have upgraded to the Vostro 1400.  Hey ho!
The Vostro 1000 is stunning value for money though.

---

### Post by Chandrashekar on 2007-08-10
Can you please tell me how to patch  ata_piix ,I have the new kernel '2.6.22-9-generic'

---

### Post by Jengu on 2007-08-12
> **chadteck said:**
> 
You will have to re-install the Nvidia driver at the very least, and your DVD-ROM will stop working.  The piix module has been removed from this kernel and ata_piix is the replacement; it requires a patch to work properly with the Vostro 1400.  If you decide to go forward with this, I can post the info regarding getting the patch applied and re-building the ata_piix module.


I'd be interested in the patch as well. Any chance it'll make it into Gutsy before release?

---

### Post by kteoh on 2007-08-13
I tried to install 7.04 alternate (regular i386). The Intel 3945 doesn't work out of the box for me--I can get signal power and everything but it fails each time to complete handshake with my router (Westell 327W). Ethernet fails to work too, which is a Broadcom Fast Ethernet BCM5906 something or another.

I tried manually installing the newer Intel drivers, except the subsystem is funky and the makefile has some errors (at least when I was trying to make patch_kernel). Does anyone have a link to the old Intel Windows drivers that work with ndiswrapper? That would be much appreciated.

---

### Post by ayu on 2007-08-14
1. Has anybody gotten the mic to work on this machine?  I'm using Dell's ([http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)) HDA intel alsa mixer for audio playback, if that makes a difference.
2. Speakers works great, and turns off when I plug a headphone into the left jack. BUT, the right headphone jack does nothing; I can't hear any audio from it.  I tried having both headphone jacks plugged in, thinking the 2nd won't work without the 1st, and still can't hear anything.  Any ideas?  Could it be because of said driver from above?

---

### Post by ayu on 2007-08-14
> **kteoh said:**
> I tried to install 7.04 alternate (regular i386). The Intel 3945 doesn't work out of the box for me--I can get signal power and everything but it fails each time to complete handshake with my router (Westell 327W). Ethernet fails to work too, which is a Broadcom Fast Ethernet BCM5906 something or another.

I tried manually installing the newer Intel drivers, except the subsystem is funky and the makefile has some errors (at least when I was trying to make patch_kernel). Does anyone have a link to the old Intel Windows drivers that work with ndiswrapper? That would be much appreciated.

My solution to fixing the ethernet was upgrading to 2.6.22-9 :eek:.  I was hoping this will also fix some of my other issues but it only fixed the ethernet.  See [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) if you are interested.

---

### Post by muadnu on 2007-08-16
I've had a Vostro 1400 for a week now, and I'm still working on some issues. But I was wondering about the CPU fan, which is running almost all the time for me, and I'm not sure it should.

I'm not sure what is the best solution, or whether I need one. Maybe I can play with the CPU frequency scaling, but I'm not sure I should. By the way, the CPU temperature is generally between 37 and 39 degrees Celsius when at a normal load (for example browsing and checking email), which I think may be a little high...

---

### Post by daageep on 2007-08-16
try to cat /proc/cpuinfo and see what speed your cpu is running at.

i am installing ubuntu literally right now so I have not messed with scaling. last i checked my cpu (core2duo 2.2ghz) is running at full speed but the fan is not on. 

try looking up the package powernowd. this is the one i always use for my intel centrino laptops. (im not sure if it is appropriate here).

---

### Post by ayu on 2007-08-16
Mine is usually scaled to 800 mhz right now (max 1.6 ghz), but the machine as a whole is WARM.  According to conky, the temperature is also around 40 C while just browsing the internet, which is hotter than I would have expected.  By the way, I think scaling works "out of the box" with Feisty.

---

### Post by daageep on 2007-08-16
Does scaling work out the box with Feisty? That's awesome.

I just finished installing Debian unstable onto my 1400. Everything works (ethernet, sound, DVD drive, 3945 intel wireless, nvidia driver, beryl, synaptics touchpad with vertical scrolling, cpu scaling) although it took me like 6 hours today to do it. i'm quite happy with everything so far. :lolflag:

I'm currently trying to test the bluetooth, webcam, and suspend/hibernate although I have no idea how those work.

Comments?

---

### Post by aldenhg on 2007-08-16
Yeah, scaling works near perfectly out of the box. The only hiccup I've noticed with it is that when it's running down at 800mhz and I go to move a window or do something with Compiz Fusion it's jerky for a second and then once it scales up it goes smooth as silk. The 1400 scales down pretty agressively to save battery life, so it'll be kinda tough to see it running full bore. 
As for the suspend, check out my other thread on the 1400 here:
[http://ubuntuforums.org/showthread.php?t=523356](http://ubuntuforums.org/showthread.php?t=523356)
Like I say in the thread, there a a few problems with sound and video and a few random things so if anyone finds a fix for any of the problems please share the love.

---

### Post by muadnu on 2007-08-16
> **ayu said:**
> Mine is usually scaled to 800 mhz right now (max 1.6 ghz), but the machine as a whole is WARM.  According to conky, the temperature is also around 40 C while just browsing the internet, which is hotter than I would have expected.  By the way, I think scaling works "out of the box" with Feisty.

Is your laptop's fan always turned on? I contacted Dell, and the guy at the chat told me that it was normal for it to be always on. I don't think that's correct, I chatted with another guy who told me that it is not normal for it to be running at full speed all the time. I'm not sure what full speed is, maybe the fan is only taking heat out all the time, and it could be making even more noise. But it is pretty noisy, and no matter if I'm just browsing the Internet or doing something more demanding, the fan is still on, and at the same speed, which I regard pretty high, with a lot of heat coming out of the side.

I scaled the CPU's frequency, now it's running usually at 800 mhz (max. 2 ghz), but there's no big difference in the temperature, and absolutely none in the fan.

By the way, I've tried running Vista, and the fan still works all the time, and I get more or less the same CPU temperatures...

So I'm wondering whether this is normal or not, if not I should just return my Vostro...

---

### Post by aldenhg on 2007-08-16
My fan runs 90% of the time, if not all the time. It's normal.

---

### Post by muadnu on 2007-08-17
> **aldenhg said:**
> My fan runs 90% of the time, if not all the time. It's normal.

Do you know if that's a thing of the Vostro or of the processor? I've used many Dell laptops, and none as noisy as this one (but this is the first one I try with a Core Duo processor). On the other hand, some other laptops I've seen with this processors (a Toshiba for ex.) seem to be be noisy too...

---

### Post by kamaboko on 2007-08-17
> **muadnu said:**
> Is your laptop's fan always turned on? I contacted Dell, and the guy at the chat told me that it was normal for it to be always on. I don't think that's correct, I chatted with another guy who told me that it is not normal for it to be running at full speed all the time. I'm not sure what full speed is, maybe the fan is only taking heat out all the time, and it could be making even more noise. But it is pretty noisy, and no matter if I'm just browsing the Internet or doing something more demanding, the fan is still on, and at the same speed, which I regard pretty high, with a lot of heat coming out of the side.

I scaled the CPU's frequency, now it's running usually at 800 mhz (max. 2 ghz), but there's no big difference in the temperature, and absolutely none in the fan.

By the way, I've tried running Vista, and the fan still works all the time, and I get more or less the same CPU temperatures...

So I'm wondering whether this is normal or not, if not I should just return my Vostro...

The time to be concerned is when you don't hear the fan.  My is on quite often.

---

### Post by kamaboko on 2007-08-17
> **muadnu said:**
> Do you know if that's a thing of the Vostro or of the processor? I've used many Dell laptops, and none as noisy as this one (but this is the first one I try with a Core Duo processor). On the other hand, some other laptops I've seen with this processors (a Toshiba for ex.) seem to be be noisy too...

My fan is pretty quiet.

---

### Post by aldenhg on 2007-08-17
Really, you shouldn't worry about your fan. Did you ever hear the fans they put in P4 laptops? Seriously, unless the fan is REALLY loud - and I'm talking hard-to-hear-over loud - you should sit back and enjoy your computer. Processors, video cards, memory and hard drives all get hot with use and if it weren't for that little fan and it's near whisper full time operation you'd burn through your lap faster through thermite through an engine block.

---

### Post by Chandrashekar on 2007-08-24
> **ayu said:**
> My solution to fixing the ethernet was upgrading to 2.6.22-9 :eek:.  I was hoping this will also fix some of my other issues but it only fixed the ethernet.  See [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) if you are interested.

I upgraded my kernel from 2.6.22-9 to 2.6.22-10 and it solved my DVD drive problem , Now the DVD drive works fine.:)

---

### Post by ayu on 2007-08-25
> **Chandrashekar said:**
> I upgraded my kernel from 2.6.22-9 to 2.6.22-10 and it solved my DVD drive problem , Now the DVD drive works fine.:)

Cool, I didn't realize 2.6.22-10 was out.  Did you update by following the Gutsy kernel script? ([http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974))
Also, do you have piix or ata_piix in your modules?  Have you tried burning a DVD yet?  Does the drive have DMA support? 
Thanks for your answers!

---

### Post by kteoh on 2007-08-28
DVD drive works for me (including burning), had to add piix back to modules.

Would be nice to get my touchpad scrolling back... :(

---

### Post by ayu on 2007-08-29
> **kteoh said:**
> DVD drive works for me (including burning), had to add piix back to modules.

Would be nice to get my touchpad scrolling back... :(

For me, upgrading to 2.6.22-10 fixed both my dvdrw and touchpad (of course I already applied the alps touchpad patch, which originally worked in 2.6.16, but not 2.6.22-9).  Cheers!

---

### Post by kteoh on 2007-09-07
> **ayu said:**
> For me, upgrading to 2.6.22-10 fixed both my dvdrw and touchpad (of course I already applied the alps touchpad patch, which originally worked in 2.6.16, but not 2.6.22-9).  Cheers!

I have it working in 2.6.20-16. I'll check if my ethernet works now, but I doubt it.
/EDIT (partially--vertical scrolling only)


One last thing that's quite annoying; has anyone gotten their speakers working?

---

### Post by saru411 on 2007-09-07
my speakers work out of the box on my vostro 1500

---

### Post by aldenhg on 2007-09-09
Did you try the intelhda stuff described earlier in the thread?

---

### Post by sparehead1 on 2007-09-14
Hi all, i just got a vostro 1400 aswell. I've scrubed vista, partitioned my drive and got ubuuntu running, cept eth0 doesn't give me much joy.

Anyway, from what I've read we can pretty much follow 1420 guides. So following that logic has anyone tryed the dell 1420 reovery cd/dvd?

I was going to try it out but i just killed my laptop half way through typing this up. power cord got tangled on chair at work and came of the desk. cracked the screen.

edit:

ISO can be found here:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Download_Dell_Ubuntu_Image)

---

### Post by briansvgs on 2007-09-15
I will test the live cd. I am looking for one without the video/piix problems anyways (I have the nvidia geforce go 8400gs, which is not recognized properly by ubuntu). Also, when I installed ubuntu feisty on my vostro 1400, it installed properly after doing modprobe piix in busybox and reconfiguring xorg for the vesa driver. However, after install, it still brings up busybox on each boot. I just type exit and it boots up properly, but I was wondering if there was any  way that I could get it to boot without starting busybox?

Thanks,
Brian

---

### Post by trash.eighty on 2007-09-17
I'm considering the Vostro 1400 with a full Intel kit (wifi, gfx, etc.) vs a Thinkpad T-series (largely because the Vostro is ~200 USD cheaper).  What I've been wondering about Ubuntu on it is:
1) I know the Intel ABG cards work well in Ubuntu, but how about their ABGN cards?  And is it really worth it to have 11n right now, or just upgrade the card later?
2) How does the suspend work?  Does it work as in "flawless" or work as in "breaks every few resumes"?
3) Is the 1.6GHz Core2duo enough for standard usage?  Right now, I'm sitting on a 2.8GHz "mobile" Celeron (NetBurst era), and it seems "fast enough" with 640MB of RAM
4) Can the Intel graphics handle light gaming?  Specifically,Quake3/WolfET, DEFCON (those 3 native), and Guild Wars under Wine.

---

### Post by briansvgs on 2007-09-18
The dell ubuntu live cd works up until X starts. If you have the nvidia card (I am assuming that it would work right with the intel video card), then the live cd still doesn't see your graphics card right. It tries to use the nv driver just like the normal ubuntu/xubuntu/kubuntu live cd, and fails to start X.

---

### Post by aldenhg on 2007-09-18
That's a known issue and the workaround is earlier in this thread. You can also use the Alternate installation CD.

---

### Post by Orion2000za on 2008-01-08
Has anyone tried to get the internal HDA modem to work? According to some posts at Dell Support this should be the same as in the 1420N but in my Vostro 1400 the kernel does not even report the modem... and I live where dial-up is still very much needed.

Sinclair :(

---

### Post by xneck on 2008-01-08
I have a Dell Vostro 1400 with Ubuntu/7.10-AMD64 and it works very well, with some issues:  
  
- You must install from Live CD in 'safe graphics mode' to display desktop (It starts with full resolution)  
- The wireless driver (ipw3945) fails some times with a 'SCAN_ABORT..' error. The connection fails after hibernation.  
- The alsa driver has a bug, you must recompile and install the latest (1.0.15). Follow the guidelines of 'Method D' from [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller). Only the internal mic not work with this method.  
- The conexant HSF modem not work because it not support the latest version of alsa at this moment (1.0.15)  
- The integrated webcam only work with well implemented v2l (as ekiga)  
- To fix the splash screen and get full resolution to the console follow this how-to:  [http://ubuntuforums.org/showthread.php?t=622018&highlight=black+screen+gutsy](http://ubuntuforums.org/showthread.php?t=622018&highlight=black+screen+gutsy)  
  
  
* Ethernet ok.
* Bluetooth ok.
* The home and multimedia buttons are assigned to rhytmbox,    
* SD/MMC ok  
* DVD ok. (tested with serpentine)
* Desktop effects ok (after installation of the nvidia driver and fix some settings with system->preferences->GL Desktop)  
* External Video not tested.

---

### Post by Orion2000za on 2008-01-14
I am using Kubuntu 7.10 on a Vostro 1400 with Intel graphics and Intel 3945 wireless. I have some annoying problems and some minor ones:

1. The kernel does not see the modem as it should so can not use it. Booting with a Knoppix liveCD and an earlier kernel can "see" the  modem codec (ls /proc/asound/card0 shows codec#0 and codec#1, for me only codec#0)

2. The intel wireless likes to play yo-yo with the connections, going on and off - ipw3945 driver

3. Suspend and Hibernate does not seem to work

minor issues: the mute and light up/down buttons don't work

any suggestions will be appreciated, I really need the modem to work

Sinclair

---

### Post by xneck on 2008-01-14
I think that the modem problem is related with the alsa version included with Ubuntu 7.10, and specifically with the snd_hda_intel module. Nothing to do until next release of Ubuntu or a new version of the conexant driver that support the latest version of alsa. You can compile and install the latest alsa driver manually, but the conexant driver refuses work with it. (Ideas?)
  
The wireless driver don't work properly. I read that a new driver is ready for the next Ubuntu (debian) stable release. The problem is  you can't use Network Manager. My wireless is WPA with a fixed IP. I needed configure it manually,and  don't use network manager to reconfigure it, or start/stop the Interface, this breaks the configuration.   
  
/etc/network/interfaces sample:  

```
  
iface eth1 inet static  #eth1 is mandatory for ipw3945  
address 192.168.XXX.XXX  
netmask 255.255.255.0  
gateway 192.168.XXX.XXX  
  
wireless-essid your.essid  
  
wpa-psk fffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff  
wpa-key-mgmt WPA-PSK  
wpa-proto WPA  
wpa-ssid your.essid  
wpa-group TKIP  
wpa-pairwise TKIP  
auto eth1  

```
  
The line "wireless-essid your.essid" is redundant but it is necessary in order that network manager show the interface in the dialog. (Make a backup copy of /etc/network/interfaces).  
  
Hibernation work for me (with the exception of the wireless connection that fails). All multimedia and function keys are ok also.   
  
I use the 64 bit version.   
  
good luck...

---

### Post by Orion2000za on 2008-01-15
Maybe we can help each other a bit... I tried to compile the latest alsa-driver and completely broke alsa, now I have no sound and reinstalling from repos do not help... any ideas what I can do?

As for the wireless: I use WICD (wicd.sourceforge.net) that deals with your wpa problem w/o any hassle. You have to do a workaround for the ipw3945 driver though, see thread "1.4.1 headaches". 

Given that Vostro 1400 is supposedly same hardware as inspiron 1420N that Dell ships with Ubuntu 7.10 I am surprised that this seems to be unsolvable (the modem problem that is). 

Sinclair

---

### Post by Orion2000za on 2008-01-15
Right, I got it sorted but it was a solution one might not choose as it replaces the kernel with Hardy kernel and the alsa-drivers with Hardy versions. 

see my other thread:
[http://ubuntuforums.org/showthread.php?t=668235](http://ubuntuforums.org/showthread.php?t=668235)

Incidentally it also fixed the problems with the FN-keys for LCD brightness adjustment and stabilised the ipw3945 wireless driver so I consider it good advice... though any update might break the whole chain I guess.

Sinclair, now happy :)

---

### Post by aldenhg on 2008-02-25
For those of you who are having problem with the Intel wifi, check out the Intel wireless website at [http://intellinuxwireless.org](http://intellinuxwireless.org). Try out the iwl3945/iwl4965 driver and see if it doesn't solve your problems. I run iwl3945 on my 3945 and it doesn't give me any of the problems the ipw driver gave me.

---

### Post by myfknight on 2008-02-28
Something about battery life: I have the 85hr battery on my vostro1400. It will last for more than 6 hours if I run vista, but only 4 hours for ubuntu--even if i turn off compiz at all time, dim my screen etc. Is it because ubuntu consumes more power or is it because of some configuration problems?

---

### Post by Orion2000za on 2008-02-29
> **myfknight said:**
> Something about battery life: I have the 85hr battery on my vostro1400. It will last for more than 6 hours if I run vista, but only 4 hours for ubuntu--even if i turn off compiz at all time, dim my screen etc. Is it because ubuntu consumes more power or is it because of some configuration problems?

I do not know what it might be but I have the 65Whr battery and get + 4 hours in Kubuntu 7.10 (Hardy kernel due to modem/alsa). I have no webcam though. 

Sinclair

---

### Post by aldenhg on 2008-03-02
I get about 5.5 hours with my 85Whr battery and I have two wireless cards and I always run Compiz.

---

