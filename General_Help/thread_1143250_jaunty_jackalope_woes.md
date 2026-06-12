---
title: "jaunty jackalope woes"
date: 2009-04-29
forum: General Help
---

### Post by FeistyStyle on 2009-04-29
I really looked forward to Jaunty Jackalope, so much so that I upgraded to the beta from 8.10 to test it early. It promised better performance and seemed as if it would just make my Ubuntu experience better.

But then it all went wrong.

Flash was jumpy
Rhythmbox playback stops, keeps going, and skips
8.10 ran cool, 9.04 runs **hot** but I see **no change in my processor load**
The entire system just locks up at times (maybe because of the heat)
and when it does lock up? ctrl alt backspace is no longer there as my best friend

I've managed to fix the flash issue with help of the forums, but this is too much.

It must just be my laptop (toshiba satellite A105 - S4094, Intel Duo 1.73, integrated intel chipset, 1.5gb RAM) 

I see no option but to downgrade back to 8.10, which I must add, ran perfectly for me.

---

### Post by gettinoriginal on 2009-04-29
I also ran into massive problems with a fresh install of 9.04 (tried two different disks).  IPv6 problems with connectivitiy, and sound/video problems.  The more I tinkered, the worse it got.  Back to 8.10 now and running great.

---

### Post by UbuntuNerd on 2009-04-29
I really want to upgrade but "Hardy" has been good to me so why replace it, you know what they say "if ain't broken don't fix it" :)

---

### Post by FeistyStyle on 2009-04-29
maybe 9.10 will break what they "fixed"

---

### Post by codeseer on 2009-04-29
> **FeistyStyle said:**
> I really looked forward to Jaunty Jackalope, so much so that I upgraded to the beta from 8.10 to test it early. It promised better performance and seemed as if it would just make my Ubuntu experience better.

But then it all went wrong.

Flash was jumpy
Rhythmbox playback stops, keeps going, and skips
8.10 ran cool, 9.04 runs **hot** but I see **no change in my processor load**
The entire system just locks up at times (maybe because of the heat)
and when it does lock up? ctrl alt backspace is no longer there as my best friend

I've managed to fix the flash issue with help of the forums, but this is too much.

It must just be my laptop (toshiba satellite A105 - S4094, Intel Duo 1.73, integrated intel chipset, 1.5gb RAM) 

I see no option but to downgrade back to 8.10, which I must add, ran perfectly for me.

I believe everybody with the intel chipsets for graphics are having similar issues. The best fix right now is to upgrade the kernel and drivers by following the instructions in this post: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by FeistyStyle on 2009-04-29
yea that was the guide I used to fix flash. Still have heat issues, sound issues with rhythmbox, and stability issues.

I've read the sound error with rhythmbox is from the pulseaudio buffer not being large enough but I am not really sure how do fix it.

---

### Post by codeseer on 2009-04-29
> **FeistyStyle said:**
> yea that was the guide I used to fix flash. Still have heat issues, sound issues with rhythmbox, and stability issues.

I've read the sound error with rhythmbox is from the pulseaudio buffer not being large enough but I am not really sure how do fix it.

I removed pulseaudio from my system.

---

### Post by FeistyStyle on 2009-04-30
yea just switching over to ALSA takes care of it but its really the heat issues that I can't understand. The processor load is low but yet the laptop gets hot. This never happened when I used 8.10 so I am not really sure what the issue is.

---

### Post by gettinoriginal on 2009-04-30
Problem solved, I went back to 8.04, then upgraded to 8.10, then to 9.04 and all is working flawlessly, no more Address not found or 404 errors.  Also have sound/video without tinkering.  This makes me very happy, but also confused, as when trying the fresh install of 9.04, I burned 3 disks from 3 different mirrors and got the same problems with each one :confused:  Anyway, problem solved, thanks to you all for your help.  If anyone is still having problems, may I suggest upgrading instead of fresh install of 9.04.

---

### Post by andy71600 on 2009-04-30
> **codeseer said:**
> I removed pulseaudio from my system.
how did you get rid of it?

---

### Post by gettinoriginal on 2009-04-30
This was written for 8.10, but should still be good, ubuntugeek is very good at keeping his site updated.
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

---

### Post by codeseer on 2009-04-30
> **gettinoriginal said:**
> This was written for 8.10, but should still be good, ubuntugeek is very good at keeping his site updated.
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

I was trying to look at my document collection to see if I had written a guide for it, but evidently I didn't. I am pretty sure I did the same things as are in that guide though. Some of the files were missing, if I recall correctly, but it still worked out just fine.

---

### Post by danebramaged on 2009-04-30
> **gettinoriginal said:**
> Problem solved, I went back to 8.04, then upgraded to 8.10, then to 9.04 and all is working flawlessly, no more Address not found or 404 errors.  Also have sound/video without tinkering.  This makes me very happy, but also confused, as when trying the fresh install of 9.04, I burned 3 disks from 3 different mirrors and got the same problems with each one :confused:  Anyway, problem solved, thanks to you all for your help.  If anyone is still having problems, may I suggest upgrading instead of fresh install of 9.04.

I upgraded from a flawless 8.10 install and 9.04 does not work with compiz properly, does not load the root terminal even though it will load a standard terminal, and loses my nvidia video settings everytime I reboot.

I am running a 3100+ amd semperon with a Gig of RAM and an nvidia 7600 GS 8x AGP card.  Fresh installs or upgrades, it looks like its pretty much hit or miss this time around.

It's too bad because, I really wanted to like this distro.

---

### Post by muhannadfa on 2009-04-30
> **gettinoriginal said:**
> I also ran into massive problems with a fresh install of 9.04 (tried two different disks).  IPv6 problems with connectivitiy, and sound/video problems.  The more I tinkered, the worse it got.  Back to 8.10 now and running great.

same same dude
9.04 no good
jaunty crappy 9.04
Ubuntu 9.04 - Jaunty Jackalope is out! [COLOR="Red"][SIZE="7"]C[/SIZE][/COLOR]rab a copy today..

---

### Post by Shamishen on 2009-04-30
I had pretty much the same problem. I updated from Intrepid a week or so ago, and my sound only worked on my headphones for a while, and then it suddenly didn't again. I downloaded the ISO and did a fresh install and now my headphones work again, but still not speakers. I can live with just headphones though, but if anyone knows a little trick or two to get my speakers working it would be appreciated.

---

### Post by gettinoriginal on 2009-04-30
> **Shamishen said:**
> I had pretty much the same problem. I updated from Intrepid a week or so ago, and my sound only worked on my headphones for a while, and then it suddenly didn't again. I downloaded the ISO and did a fresh install and now my headphones work again, but still not speakers. I can live with just headphones though, but if anyone knows a little trick or two to get my speakers working it would be appreciated.

hope these help::P
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506) 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

