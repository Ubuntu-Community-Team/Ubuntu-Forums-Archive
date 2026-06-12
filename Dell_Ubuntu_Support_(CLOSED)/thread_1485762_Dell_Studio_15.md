---
title: "Dell Studio 15"
date: 2010-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ilovelinux33467 on 2010-05-17
Hi

I have ordered my new laptop last thursday (Dell Studio 15) and I wanted to know if everything worked with it out of the box on Ubuntu. Also would be a great benefit if I installed fglrx (ATi HD4750)?

Thanks

---

### Post by Joshcush on 2010-05-17
I have a studio 1555. I would recommend using Karmic instead of lucid for the time being.

I have had a several issues withe 10.04  the biggest being the inability to resume from either suspend or hibernate without a full restart. I have had to disable sleep when the lid gets shut just to be able to use my computer, and unfortunately my battery life has suffered as a result. From my research, the problem is widespread on studio's and no fix is currently available to my knowledge. 

I can tell you that 9.10 with the ati 4750 and the proprietary driver runs beautifully. The only issue I had was getting the media buttons to work, but it was an easy fix.

[http://ubuntuforums.org/showthread.php?t=1409151](http://ubuntuforums.org/showthread.php?t=1409151)   (fix for media buttions in 9.10)



If you care about full screen flash video, It works fine on 10.04 but I could never get 9.10 to play without stuttering.


I hope this helps.


My specs if you care: Intel Core 2 Duo p8700 (2.53Ghz)
 Ati 4750 512 mb, 4Gb 800mhz DDR2, 500Gb hdd 7200 rpm

---

### Post by ilovelinux33467 on 2010-05-17
Thanks for the advice. Hope they get these issues fixed with Lucid soon. Does anybody know if these issues are in the upcoming Fedora 13?

Thanks

---

### Post by ilovelinux33467 on 2010-05-17
Thanks for the advice. Hope they get these issues fixed with Lucid soon. Does anybody know if these issues are in the upcoming Fedora 13?

Thanks

---

### Post by ilovelinux33467 on 2010-05-17
Sorry for the double post. Something happened :confused:

---

### Post by Maheriano on 2010-05-17
I have the Studio 15, the same one you ordered, I got mine a year ago. For me everything works perfect in 10.04, never had a problem at all. I also upgraded to the ATI HD3450 video card though I haven't tried HDMI out yet.

And for me I disabled the sleep function when I close the lid so I don't have the resume issues mentioned by someone else, I just opened the lid and start typing.

---

### Post by ilovelinux33467 on 2010-05-17
if I upgraded the kernel in Lucid from 2.6.32 to 2.6.33 or the 2.6.34 RC will I experience the same issue?

---

### Post by Rackstar on 2010-05-19
I just received my Studio Dell 15 today, and I have several issues on 10.04:

- Bluetooth device not recognized
- Sound not working through headphone jacks
- Wireless is pretty unstable

Graphics running perfect though...

---

### Post by venkidwaraka on 2010-05-21
@Rackstar
I own a Dell studio 1558.
I also faced similar issues which you have pointed out.
But I was able to remove the last 2 issues but couldn't fix the bluetooth yet.
The problem with the wireless is that when we press the wireless button it doesn't get initiated at that instant. We have to go on tapping it for some number of times and if we are so lucky enough, we could get it started the very first time itself.

Fixing wireless problem
Go to System>Administration>Hardware Drivers
It will automatically search for any proprietary drivers available and list it in Ubuntu 10.04- Lucid. Installing that will fix the issue of wireless being not working.

Fixing Sound problem - Jack
Just visit this link to solve that issue
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Please do not forget to post the solution for bluetooth problem if you get one.

Thanks
Venki!!

---

### Post by Rackstar on 2010-05-21
> **venkidwaraka said:**
> @Rackstar
I own a Dell studio 1558.
I also faced similar issues which you have pointed out.
But I was able to remove the last 2 issues but couldn't fix the bluetooth yet.
The problem with the wireless is that when we press the wireless button it doesn't get initiated at that instant. We have to go on tapping it for some number of times and if we are so lucky enough, we could get it started the very first time itself.

Fixing wireless problem
Go to System>Administration>Hardware Drivers
It will automatically search for any proprietary drivers available and list it in Ubuntu 10.04- Lucid. Installing that will fix the issue of wireless being not working.

Fixing Sound problem - Jack
Just visit this link to solve that issue
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Please do not forget to post the solution for bluetooth problem if you get one.

Thanks
Venki!!

Hey,

Thanks for your answer! I haven't found an answer for the bluetooth problem, but that isn't such a big problem for me, as I only use it for transferring files from and to my phone, but I can use USB as well.

Currently I'm trying to get the "switch monitor"-key working. No luck yet. (Fn - F1)

---

### Post by Rackstar on 2010-05-21
> **Rackstar said:**
> Hey,

Currently I'm trying to get the "switch monitor"-key working. No luck yet. (Fn - F1)

I managed to write a workaround for this problem:
[http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932](http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932)

---

### Post by ilovelinux33467 on 2010-05-28
Ok I got the laptop and upgrading the kernel to 2.6.34 fixed the issue with closing the lid. It now doesn't freeze when you close the lid :)

Only problem fglrx doesn't work with 2.6.34 :( but the open source ati drivers are really good and play nexuiz well but it would be nice to use the propriatry ati drivers.

---

### Post by Rackstar on 2010-05-28
> **ilovelinux33467 said:**
> Ok I got the laptop and upgrading the kernel to 2.6.34 fixed the issue with closing the lid. It now doesn't freeze when you close the lid :)

Only problem fglrx doesn't work with 2.6.34 :( but the open source ati drivers are really good and play nexuiz well but it would be nice to use the propriatry ati drivers.

I read about a fix for suspend, and it works for me! It is really really simple. Setting desktop effects to 'extra' fixes it.

---

### Post by ilovelinux33467 on 2010-05-28
> **Rackstar said:**
> I read about a fix for suspend, and it works for me! It is really really simple. Setting desktop effects to 'extra' fixes it.

Really, is that all you need to do? enable compiz? Hmmm strange fix but if it works all well ill be happy to give it a go :)

---

### Post by Rackstar on 2010-07-28
> **ilovelinux33467 said:**
> Really, is that all you need to do? enable compiz? Hmmm strange fix but if it works all well ill be happy to give it a go :)

Yea, after some this workaround stopped working.

Anyone else found a solution for suspend/resume? I hoped it would come through updates.

Thanks

---

### Post by Rackstar on 2010-07-28
Ok, something stupid, I was suffering from this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477106](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477106)

"lucid alpha-2 and earlier freeze upon suspend with sd card plugged in with some hardware"

Leaving out my sd card fixes it.

---

