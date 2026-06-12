---
title: "I know what you're going to say..."
date: 2009-06-13
forum: General Help
---

### Post by thaumielx72 on 2009-06-13
... You're going to tell me my box is toast and to start saving for another computer.

But, just in case anyone has an alternate plan I will tell you my story.

I have a HP desktop (m370n) which I put my old computer's hard drive in.  I then loaded Ubuntu 7.10 on the old drive C: and let grub decide whether to go with Ubuntu (most of the time) or stick with Winblows Vista (I cannot live without my COD4 [and beer] on weekends).  Sad, I know.

After a year of this merry setup I was told by my Windows anti virus program that I might wanna reboot here and clear all the system.  I thought this could wait.  The next time i tried to reboot Ubuntu froze almost immediately. I tried to reboot again and the desktop kept trying to read from the hard drive for a couple minutes and then just stopped there.

After checking a couple of forums (on my good ol' still working laptop) I disconnected everything but the monitor, keyboard and mouse and tried to reboot again - this time with the Ubuntu CD I used to load 7.10 onto the old hard drive with.  I even opened the box and disconnected the two hard drives.

It never even gets to the screen (from HP) giving me the option of recovering from CD or going to safe mode.  In fact, the monitor never shows anything.  It waits for a minute or so then goes to sleep mode like it is just plugged in and not attached to any computer.

I can see it trying to read the CD/DVD drive with Ubuntu 7.10's boot disk but it never shows up on the screen.  I know the monitor is still working because it is mirroring this screen as I type this on my laptop. 

I have had computers shot out from under me before so I guess I'll live but I am open to any suggestions.

It looks like some virus fried my BIOS but nobody knows more about computers than Ubuntu geeks so I thought I would listen to you guys before just throwing the whole ($1500) setup away.

Thanx in advance for any help.

---

### Post by synapsys on 2009-06-13
Very rare that a virus could nuke your bios... although i suppose it's possible. I would start by checking your ram.... if you have multiple sticks remove one by one..... or swap for known working ram...... also you can try removing and replacing the cmos battery..... (looks like a watch battery) next check power supply, motherboard, cpu..... process of elimination.

If you don't feel comfortable cracking the case of your hp.... have somebody else do it.

---

### Post by TrakerJon on 2009-06-13
Hmmm sounds like the motherboard might be toast but it could just as easily be the video card or chipset. install or swap out a video card. Are you getting any beeps? Try resetting the CMOS from the documentation for your mobo (HP tech support will only make you want to kill someone). If it were RAM you would probably be getting beeps of some sort. The power supply could also be toast which would be one of the cheapest options to explore.

---

### Post by synapsys on 2009-06-13
Unless your RAM is totally fried.... not allowing system to POST.... in which case you will get no beeps......

---

### Post by donkyhotay on 2009-06-13
Try pulling out the HD and then booting from the liveCD. A faulty HD can often confuses the HP BIOS system which causes it to lock up at POST (I've experienced this personally). Removing the faulty HD fixes this though of course you need a liveCD to boot and your data is gone.

---

### Post by CatKiller on 2009-06-14
While you're in the case, it's worth checking the motherboard for bulging/vented capacitors. You might also want to try booting with one RAM module at a time, in case one has failed. The power supply is a possibility, so if you've got a known good replacement you could try that too.

---

