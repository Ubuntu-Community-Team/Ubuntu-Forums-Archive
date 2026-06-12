---
title: "Inspiron 1525 with 9.04"
date: 2009-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wgarider on 2009-04-28
Installed Jaunty last night - here's the status......

_The Good:_
-Wireless worked right out of the box! *(unlike 8.04 - grrrr)*
-FAST BOOT - wow!
-Installed Cheese after initial OS install and the camera works fine.
-Sound - don't make the mistake I did and try and fiddle with it. Mine works with the default settings. Leave it alone.
-Firefox needs Flash Player installed
-Rhythmbox is hosed for playing MP3's off my Widnows server share. Copying them locally or playing off a USB drive, no problem.
-There is an excellent multimedia thread in the folder here on the forums that describes how to get additional codecs, libraries, and whatnot - I followed it and it was great.
-Intel video card is now apparently on the blacklist - I can only use the 'normal' visual effects now.... ;-(

Bottom line is that a default 9.04 install is fine and IMHO, boots MUCh faster. Great hardware support in this distro - Kudos to everyone on the 9.04 team wow!

---

### Post by Spooky5 on 2009-04-28
Please do, I have a 1525n and have been waiting to see if there were any problems before I decided to update.

---

### Post by wgarider on 2009-04-28
> **Spooky5 said:**
> Please do, I have a 1525n and have been waiting to see if there were any problems before I decided to update.

UPDATE: Sound is okay through the jack (headphones), speakers are a bit weak....

All the buttons above the keyboard seems to work fine.....didn't try to use the 'home' button though........

---

### Post by superm1 on 2009-04-28
> **wgarider said:**
> UPDATE: Sound is okay through the jack (headphones), speakers are a bit weak....

All the buttons above the keyboard seems to work fine.....didn't try to use the 'home' button though........
Check *all* of the mixers.  There may be a "front" or "speaker" mixer that isn't adjusted by default to be high enough.

---

### Post by wgarider on 2009-04-28
> **superm1 said:**
> Check *all* of the mixers.  There may be a "front" or "speaker" mixer that isn't adjusted by default to be high enough.

Good call - I found one setting on the volume control that appears in the panel that didn't match. Do I need to reboot after changing that?

---

### Post by superm1 on 2009-04-28
> **wgarider said:**
> Good call - I found one setting on the volume control that appears in the panel that didn't match. Do I need to reboot after changing that?
Nope, those mixers are live settings

---

### Post by Canobuntu on 2009-04-28
Hi
Can I just confirm what is and is not working. I also have an Inspiron 1525n and have delayed updating until someone has got all the wrinkles ironed out. Sounds like its going well - where did you get with teh volume. Is it all working now?


Thanks


Tim

---

### Post by wgarider on 2009-04-28
> **Canobuntu said:**
> Is it all working now?


Nope - everything was worked out, then there were sound issues. Going to try again this evening to reinstall.....I'll post back here later.

---

### Post by TurinPT on 2009-04-28
Hey have you managed to get compiz working?
This is what I get on my 1525:

```
turin@turin-laptop:~$ compiz --replace&
Checking for Xgl: [1] 7680
turin@turin-laptop:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by usstitan on 2009-04-28
hi, i have a dell 1525n and i have updated it to 9.04. the computer is running fine and no big problems so far. The only minor problems i do have is that i have the intel graphics chip and i can't enable normal or extra visual effects but the computer is running fine without it so not really bothered about it (plus it does give a warning about intel graphics in the release notes so was expecting it) And also, not really sure what is causing this but not really looked into it, when the computer has finished booting up it takes about an extra 30 seconds to find my wireless network and connect to it (used to find it instantly in 8.10). So no really big issues but the wireless delay is something else to put on my to do list, not bothering me at the moment but may do some day.

---

### Post by TurinPT on 2009-04-28
> **TurinPT said:**
> Hey have you managed to get compiz working?
This is what I get on my 1525:

```
turin@turin-laptop:~$ compiz --replace&
Checking for Xgl: [1] 7680
turin@turin-laptop:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
```
Ok it turns out the card is blacklisted, which is odd since it worked fine on 8.10.

This fixed it for me:
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

### Post by jman1013 on 2009-04-28
Installed 9.04, works great (even the sound), BUT my wifi card does not work. It is the embedded one (it came with the laptop). The wifi switch on the side does nothing and the wifi indicator light does not turn on. I REALLY need the wifi so any help would be appreciated. 

Other than that 9.04 works great.

jman1013

---

### Post by wgarider on 2009-04-28
> **usstitan said:**
> hi, i have a dell 1525n and i have updated it to 9.04. the computer is running fine and no big problems so far. The only minor problems i do have is that i have the intel graphics chip and i can't enable normal or extra visual effects but the computer is running fine without it so not really bothered about it (plus it does give a warning about intel graphics in the release notes so was expecting it) And also, not really sure what is causing this but not really looked into it, when the computer has finished booting up it takes about an extra 30 seconds to find my wireless network and connect to it (used to find it instantly in 8.10). So no really big issues but the wireless delay is something else to put on my to do list, not bothering me at the moment but may do some day.

I ended up reloading 9.04 and have almost a carbon-copy of your experience. No more issues, only a missing plugin for Firefox and Rythmbox won't play my MP3s.....

---

### Post by wgarider on 2009-04-28
> **TurinPT said:**
> Ok it turns out the card is blacklisted, which is odd since it worked fine on 8.10.

This fixed it for me:
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

Same deal I had - can't use the fancy graphics effects but I can live without them.......

---

### Post by wgarider on 2009-04-28
> **jman1013 said:**
> Installed 9.04, works great (even the sound), BUT my wifi card does not work. It is the embedded one (it came with the laptop). The wifi switch on the side does nothing and the wifi indicator light does not turn on. I REALLY need the wifi so any help would be appreciated. 

Other than that 9.04 works great.

jman1013

Yours is a 1525? I think there were only two kinds of wifi that came with it - one was a broadcom and I don't remember the other. I have the Broadcom and it works fine......

---

### Post by jman1013 on 2009-04-28
> **wgarider said:**
> Yours is a 1525? I think there were only two kinds of wifi that came with it - one was a broadcom and I don't remember the other. I have the Broadcom and it works fine......

I have the Broadcom as well.

---

### Post by wgarider on 2009-04-28
> **jman1013 said:**
> I have the Broadcom as well.

Search the forums for past posts on Dell + Broadcom....I know there were some "how to" guides posted....

Not sure how I can help but I'll be happy to compare system configs if it will help.....

---

### Post by jman1013 on 2009-04-29
The wifi worked in 8.10 (after the first update) so I'll install it then upgrade to 9.04. Hopefully the wifi will carry over. If not, I'll just stick with 8.10.

Thanks for the help,
jman1013

---

### Post by TurinPT on 2009-04-29
> **jman1013 said:**
> Installed 9.04, works great (even the sound), BUT my wifi card does not work. It is the embedded one (it came with the laptop). The wifi switch on the side does nothing and the wifi indicator light does not turn on. I REALLY need the wifi so any help would be appreciated. 

Other than that 9.04 works great.

jman1013
This is what I used to get wireless back in 8.10: [WifiDocs Driver bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions")

---

### Post by suryakalyan on 2009-04-30
I have DELL 1525 and things are working fine apart from the sound which seems to be very low.
 
Have not installed many packages. Going to try them over the weekend.
 
But Ubuntu 9.04 seemed to be a very basic OS for me. Can we have some fancy eye candy graphics packages installed? Where can I get them?

---

### Post by bolex100 on 2009-04-30
I am unclear about this thread.  Is it about a NEW install of   9.04 or an upgrade from 8.10 or a brand new machine? Some of these issues (like low volume) seem to be normal n1525 issues.

---

### Post by wgarider on 2009-04-30
> **bolex100 said:**
> I am unclear about this thread.  Is it about a NEW install of   9.04 or an upgrade from 8.10 or a brand new machine? Some of these issues (like low volume) seem to be normal n1525 issues.

Mine was a clean install.......

---

### Post by usstitan on 2009-04-30
Mine was a clean install on a 1525 that is 5 months old. And i have no sound issues. Only thing i had to do sound wise was on the mixer put front up to max and that fixed the low volume.

---

### Post by CoreyB. on 2009-04-30
I have a Dell Inspiron 1525 and with Jaunty, when the computer is shut down or rebooted while connected to a wireless network, it won't complete the shutdown.  The Usplash shows up and the progress bar moves all the way to the right like it is supposed to but then the screen is just black and the power light and Bluetooth light are still on.  My brother and I have the same laptops and are having the same issue.  This problem did not occur with Intrepid.

Anyone else have this issue or know how to troubleshoot it?

Thanks a bunch!!

---

### Post by wgarider on 2009-04-30
> **CoreyB. said:**
> 

Anyone else have this issue or know how to troubleshoot it?

Thanks a bunch!!

I'm not having that issue.....the one I AM having is where about 50% of the time I don't automatically connect to my access point....weird....

---

### Post by cipicip on 2009-05-01
Hi guys! I was wondering if any of you tested the dual screen. Is it still working in 9.04 considering the issues with the video card? I have a big monitor with HDMI so would be nice to know if I'll still be able to use it after upgrading from 8.10

Thanks.

---

### Post by bolex100 on 2009-05-01
> I have a big monitor with HDMI 
You have an HDMI that WORKS?  cool!

---

### Post by usstitan on 2009-05-01
My hdmi works, well the picture anyway, no sound though.

---

### Post by lucraft on 2009-05-03
Installed fine. Wifi works, sound works, this gave me desktop effects again: [http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112).

That there are Intel driver issues is slightly annoying, considering I bought an Intel graphics laptop specifically so that I could use desktop effects in linux (I've previously had two supposedly supported ATI Radeon cards that never worked once). What exactly should we be using?

Anyway, fantastic that it's been two installs now without any WiFi issues at all. Fantastic that I can now trust my laptop to work with any projector output (works even better than the Macs in the office now!)

---

### Post by Spaced on 2009-05-14
Hi everybody,

I have a Dell Inspiron 1525 as well, and after _upgrading_ to Jaunty I have no sound. I've tried to compile the newest alsa drivers (solution which worked in Intrepid) but to no avail. I've tried to add an infinite number of possible options to the /etc/modprobe.d/alsa-base.conf file, but no one worked. I've tried to set the output to PulseAudio, ALSA, OSS, but none of them works, and not even the headphones work (as it is for someone, I've read). Still, the annoying system beep is up and running...

---

### Post by wgarider on 2009-05-15
> **Spaced said:**
> Hi everybody,

I have a Dell Inspiron 1525 as well, and after _upgrading_ to Jaunty I have no sound. I've tried to compile the newest alsa drivers (solution which worked in Intrepid) but to no avail. I've tried to add an infinite number of possible options to the /etc/modprobe.d/alsa-base.conf file, but no one worked. I've tried to set the output to PulseAudio, ALSA, OSS, but none of them works, and not even the headphones work (as it is for someone, I've read). Still, the annoying system beep is up and running...

A clean install seems to be the way to fix the sound....

---

### Post by delkarrr on 2009-09-07
Hi.  I have the same computer as you (Inspiron 1525/Core2Duo 2.0 Ghz/3GB RAM/250GB HD/9.04/Jaunty), but when I use my HDMI cable, the sound only comes through the computer speakers,and not through my TV, yet the picture comes out fine on the TV.  Any ideas?

---

