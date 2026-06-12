---
title: "dell 8600c won't boot when using battery"
date: 2007-06-01
forum: Dell  Ubuntu Support
---

### Post by george29 on 2007-06-01
Hi Guys, 

I recently got around to installing Feisty on my laptop - Dell inspiron 8600c, 2.0Ghz pentium M, 512Mb RAM, Dell truemobile 1450 wireless (broadcom chip). As far as i can tell everything is working as it should, getting the wireless set up with WPA took a fair bit of faffing and i've yet to work out how to set it up to allow the use of other access points other than my home connection. 

My problem is that when the laptop is connected to the mains power supply it boots correctly. if however i try and boot without mains *i.e.* just using the battery it starts to boot and the stalls at the ubuntu boot screen with the progress bar. 


How can i start to diagnose what is causing this and go about fixing it?

Hope someone can help.

-----------------------------------------------------------------------------------------
have been back and attempted to boot using the battery (which i know is charged and fine - works when i boot into XP) using the recovery mode grub option...
the boot sequence appears to be falling over after loading of kernel modules and attempting to load the manual modules for ndiswrapper to get my wireless card working... anyone have any ideas why this happens on battery power but not on mains?


George

---

### Post by mike_b on 2007-06-02
I have the exact same problem.  Running an up-to-date Feisty with 2.6.20-16-generic.

It fails during "* Loading Hardware Drivers..." but I do not use ndiswrapper, and testing it two times, it hung at different times.  Once after loading usbcore, and once after loading nvidia.  It fails even booting into the recovery mode.  So its not a driver issue.

I did find a work around.  The boot up only fails on a cold boot.  Pressing CTRL+ALT+DEL at the grub screen and forcing a warm-reset before Ubuntu starts booting gets past the problem.  Maybe we should file a bug report.  I'm using similar hardware, different model Dell laptop though.

---

### Post by bapoumba on 2007-06-03
Thread moved to "Ubuntu Dell Support" sub forum.

---

### Post by Rescue9 on 2007-06-05
I'm also having this problem with my 8500. I'm wondering if the bios is putting something into a power save mode and ubuntu is hanging when trying to detect. I'll try disabling my wireless and bluetooth with Fn+F2 to see what happens. The problem I'm having now is that the laptop is warm and I can only replicate this problem when it's been sitting off and cools down.

---

### Post by Rescue9 on 2007-06-07
I've been doing a bit of experimenting and I've found something out. Don't ask me why cause I can't explain it but here's what I found.

I have my grub set to default out after 10 seconds. If I choose Ubuntu without letting the default timer finish it fails. However if I let grub default out after 10 seconds it boots fine. I'm thinking that maybe this gives hardware time to "wake up" or "warm up" after a cold boot.

Just a though.

---

### Post by george29 on 2007-06-12
> **Rescue9 said:**
> I've been doing a bit of experimenting and I've found something out. Don't ask me why cause I can't explain it but here's what I found.

I have my grub set to default out after 10 seconds. If I choose Ubuntu without letting the default timer finish it fails. However if I let grub default out after 10 seconds it boots fine. I'm thinking that maybe this gives hardware time to "wake up" or "warm up" after a cold boot.

Just a though.

I've just done a quick test on my laptop and it behaves in the same way i.e. if i let the boot progress naturally, wait for grub to countdown from 10 and start ubuntu everything loads and it all works fine.
If i try and force start the boot then it hangs at loading ndiswrapper. this is  with a warm laptop - i'll try again later when it's had time to cool down, to see if is repeatable from a proper cold start.

i've no idea whether this is a linux bug or a dell bios issue with hardware not initializing fast enough. 

Is it worth filing as bug?


George.

---

### Post by gcraney on 2008-07-14
I have this problem in my new Ubuntu Hardy Heron.  I am using a DV2419us (HP)

So it would seem that this isn't really a Dell hardware issue.  I have not tried much to fix it. I installed Ubuntu over the weekend and now I am at work and just experienced this problem when I tried to use the laptop off of battery.  I had it plugged in through all the setup.  I will experiment with what you all have said.

I used ndiswrapper to get my wireless to work.  I have some Compiz stuff turned on and I am using VMware to run XP.  The machine is also a dual boot with Vista.

Thanks,
G

========
So I have done some experimentation and discovered that if I let it count down past 3 it works just fine.  before that it doesn't work.  Basically the longer I let it wait the happier it is.  Weird...

---

### Post by gcraney on 2008-07-17
So I got all the stuff I wanted in Ubuntu on this HP, but it wasn't stable.  I had this battery/boot problem, my wireless card couldn't stay connected to a WPA Enterprise connection, along with a couple other glitchy acting things.

I bookmarked the guides that worked well on my desktop and then went and reinstalled Ubuntu.  When I was setting it up I only followed the guides that worked. (ie I went straight to ndiswrapper instead of trying BCM43xx fwcutter business first  -I have a BCM4328 so this was necessary) Anyway, I did everything very meticulously and carefully and this install doesn't have problems w/ that freezing business.  I can boot just fine even if I only have 15% battery left.

I hate to say it, but maybe try a very careful reinstall....It seems to have fixed my problem.

---

