---
title: "Dell 620 video driver issues...."
date: 2010-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by w2ge on 2010-09-05
Let me start as others have...** I am a TOTAL NOOB when it comes to Ubuntu Linux.**..  (Windows, that's another story!) First time using it, but so far loving it...  except for the following issue.

Anyway I got a hold of a free Dell 620, grabbed a semi-new HD and installed Ubuntu 10.04.  I cannot see the "taskbar", "launch bar" (whatever you want to call it! ;-) on the laptop. (very bottom of screen seems cut-off) I went to system>adm>hardware drivers and 3 Nvidia options were found. Installed the recommended option but upon reboot got a large error screen about some X-driver reload insructions (googled the error but came back with instructions from 2007)... and option to load once in low graphics mode.  I tried this and that and tried all the versions of Nvidia drivers offered until one totally froze the machine at boot and I could DO NOTHING! Stuck at UBUNTU screen.  GRRRRR!    I finally did a total wipe/reload  and am still stuck with 1024/768 res. and am missing the bottom toolbar/notification/quicklaunch, etc.... that shows what programs are loaded etc...

Didi a search and it was back to 2007...  dif. version.. and I didn't quite understand what to do...  Any help, greatly appreciated!! TIA, Phil  (aka Ubuntu Noob of the year!) :)

If it means anything, I just rebooted and this time the lower bar DOES show.. so it seems intermittent. I also ran LSPCI to find out the video card:

nVidia G72M (Quadro NVS 110 GeForce Go 7300)  I am a little suspicious that perhaps the videocard  is "flaky" on this MB, I get those weird lines on the screen/flashes often upon boot that are indicative (to me) of video issues...(?)
[B]
FINAL: MB was the issue, Dell sent a refurb MB for free, installed MB, re-installed 9.10 and all is good in the world now![/B]

---

### Post by mörgæs on 2010-09-06
Hi, welcome to Ubuntu.

If you want to examine your video card the easy way, you could try a live boot with Ubuntu 9.10 and/or other Linux distros for comparison.

---

### Post by w2ge on 2010-09-06
Margaes, So your point is that possibly 10.04LTS may have some compatibility issues with  this video and if I use the earlier version (9.10) we can see if there is any change?

I think I get ya!

 TIA, Phil

(Well, looks like I need to download, burn 9.10!)

---

### Post by w2ge on 2010-09-06
When I go to sysrem > preferences > monitor I get this as the error message:


[I]
You do not appear to be using the nVidia X driver.  Please edit your X configuration file  (just run 'nvidia xconfig' as root), and restart the X server.[/I]

TIA,


P.S. I'm also going to search the error

---

### Post by Baji P. on 2010-09-06
Phil, which 10.04 CD did you use ? Desktop or Alternate ? 32-bit or 64-bit ?

Also was your laptop connected to the net via wired ethernet during the install ? this is particularly important during installation.

I recently did an install on a machine with an nVidia video, at the end of which I received a notification to update my video driver using a vendor supplied driver. I am not opposed to vendor supplied drivers, but I chose to ignore the driver this time. Ubuntu needed to update a few other packages, I allowed that. When it was all done, the notification disappeared and everything is working just fine.

Your mileage may vary, good luck & welcome to Ubuntu & Linux.

-baji.

---

### Post by w2ge on 2010-09-06
Baji, I used 10.04 LTS 32 bit (desktop ? what's the difference?)  On my first install I was connected via wired ethernet.  After trying various nVidia drivers and totally freezing the machine I reloaded and was wireless that 2nd time. After all was done I downloaded all the found upgrades (like 270!) and again ran hardware drivers...  but I often get the error message that I had a video driver error and to run in low-graphics mode one-time....  the "dockbar" then appears but I'm stuck in 1024/768 res...not very sharp graphics...

I did a search and found a similar issue and went to terminal and did the sudo nvidiax config (something like that command) and got an error message that xconifg was missing and a new one was loaded or installed.. can't quite remember.  Rebooted and got the video error message again....  I'm still stuck.  I was thinking of trying ver 9.1 booted of disc as was suggested by Morgaes to see what happens..  

Thank you for the Warm Welcome, BTW.

Still Perplexed,

Phil

---

### Post by Baji P. on 2010-09-06
Phil, the desktop CD contains a live file system so people can evaluate the distro without modifying their hard disk. So they can choose whether or not to install on the hard disk. Obviously this takes up space on the CD, so there are fewer drivers & packages on the desktop CD.

The alternate CD only includes options to install on the hard disk, it uses a text based installer and contains more installation oriented content. Anytime you experience installation issues, the alternate CD is your best bet.

32-bit was the right choice for now.

If Morgaes's suggestion resolves the issue, Great !

Otherwise if you have the patience, try the 10.04.1 alternate install CD with a wired ethernet.

[http://ubuntu.mirrors.tds.net/pub/releases/10.04.1/ubuntu-10.04.1-alternate-i386.iso](http://ubuntu.mirrors.tds.net/pub/releases/10.04.1/ubuntu-10.04.1-alternate-i386.iso)

If that doesn't work & you are feeling really lucky, you might try this puppy too :

[http://ubuntu.mirrors.tds.net/pub/releases/maverick/ubuntu-10.10-beta-alternate-i386.iso](http://ubuntu.mirrors.tds.net/pub/releases/maverick/ubuntu-10.10-beta-alternate-i386.iso)

Good luck !

---

### Post by w2ge on 2010-09-07
Well, I tried 9.10 both as disc and then did an install.. tried dual-boot leaving 10.04lts on but gave kernel error...  onwards it went and did install 9.10 (solo) and graphics were generic but I got 1440/9** or whatever, MUCH BETTER!  However, it froze anytime I minimized Firefox, tried to open certain applets...  GRRRR!

Back to installing 10.04lts...  THIS SUCKS, I'm starting to think it is hardware related...

10224/768 looks so crappy and missing dockbar (intermittently) is a PIA!  :(

---

### Post by mörgæs on 2010-09-07
Here is something on installing Nvidia drivers:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by w2ge on 2010-09-07
Well, I think I've gotten to the bottom of this (I HOPE!!)  I was googling the D620 and nVidia video issues and found out that they (Dell) extended the warranty on this model becuase of the high failure rate of the nVidia chip!  I put in my service tag and saw that I was out of warranty (it had lapsed in March of this year)..  I decided to try b*tchin anyway, got Dell Chat on and told the guy that I had lines on the screen and it was blue-screening and I was seeing what looked like a video .dll error message.  He asks me to wait a few minutes and comes back and offers to send me a new Motherboard, no charge!

I can change it in an hour or so (if no one bothers me!)  Maybe my frustrations are over!

:)

Thanks!

---

### Post by Baji P. on 2010-09-07
Phil, I hope that resolves the issues you were having. If it was a failing nVidia chip that caused all these problems, that would make me really mad. Let us know how the MB change works out.

---

### Post by w2ge on 2010-09-12
FINAL:  Dell overnighted me a refurb exchange  board for free, installed the MB... had to reload (probably due to BIOS  issues, this one had newer version) used older Ubuntu 9.10 and NIGHT and  DAY! 
 
No doubt the video on the old MB was the issue, now works perfect, I'm  at 1440/900 res. and it is stable and is FREAKIN AWESOME!!! 
 
Talk about fast, simple...

Thanks All. 

:D 

 Now if only I could run Garmin Mapsource under Linux....

---

