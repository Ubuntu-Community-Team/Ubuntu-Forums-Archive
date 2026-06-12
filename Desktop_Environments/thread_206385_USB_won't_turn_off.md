---
title: "USB won't turn off"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Doovoo on 2006-06-30
This is something I've been dealing with since the last time I installed Dapper. For whatever reason, when the computer shuts down, it doesn't cut the power to the USB ports (leaving my mouse, keyboard, and wacom tablet on).

This is probably an easy fix, I just haven't seen anything about it. Help?

---

### Post by YourDoom123 on 2006-06-30
I'm not 100% certain, but this doesn't sound like a bug in dapper. once the comp shuts down, the OS has nothing to do with what goes on. actually, i don't think what your experiencing is any sort of bug at all. Your computer's power supply isn't turning off, so its powering the usb ports, which in turn power the mouse, keyboard, etc.. now, i could be wrong, about that, but in most modern computers, the power supply doesn't turn off until you manually turn it off by reaching around back and flipping a switch. either way, flipping that switch will fix your issue. you have to flip the switch back to turn the comp on tho.

EDIT: this assumes that the computer is actually shutting down. if its not, then that IS a problem with the OS.

---

### Post by Lil_Eagle on 2006-06-30
> Your computer's power supply isn't turning off, so its powering the usb ports, which in turn power the mouse, keyboard, etc.. now, i could be wrong, about that, but in most modern computers, the power supply doesn't turn off until you manually turn it off by reaching around back and flipping a switch. either way, flipping that switch will fix your issue. you have to flip the switch back to turn the comp on tho.


That's not only true with computers, but most new electronic devices.  They all have "standby" mode (TV, VCR, DVD, Playstation).  Even when you turn them off they aren't off.  Is it a conspiracy?  Do the hardware manufactures have a connection with the utility companies?  Some might think so.  There is no good reason for this to be so.  

On the other hand, I kind of like the Christmas tree when I turn off the lights in the evening.  Between the lights on the computer, speakers, router and the blinking light from the optical mouse, it is quite entertaining.  If I shutdown the computer, the only light that goes out is the pretty green one on the front of the computer.  The rest stay on unless I manually flip a switch.

Seriously, you can always put your computer on an UPS, which is a good thing to do anyway.  Then when you're done with the computer, turn the UPS off.   Conversely, you can also just leave everything on.  Computers don't use too much power if they aren't busy and the power management software has cut power to many of the devices inside.  Leaving it on means you don't have to wait for it to boot.  It will be ready and waiting for you when you are ready to use it.  It also means you can set cron jobs to do things like backup or download in the middle of the night so they don't interfere with your work.

---

### Post by Doovoo on 2006-06-30
This is what I initially thought was going on, but it led me to the following question - why do they turn off when I shut down Windows? Unless the OS is telling something to the system, I have no idea why there'd be any difference.

---

### Post by chrisccoulson on 2006-07-18
I am seesing exactly the same problem with my machine. When I shut down Dapper, all my USB devices remain powered. But when I shut down Windows, they all turn off. It's a little annoying because I have a USB gaming pad and joystick which keep the room lit up at night.

---

### Post by Paki on 2006-07-21
I have the same problem with USB devices staying powered. USB power is turned off when Windows shuts down the system, and USB power used to turn off when Ubuntu 5.10 was shutting down the system.

I notice that another linux distrobution gives me the same problem. It makes me wonder if the issue isn't in Linux kernel 2.6.15?

---

### Post by Haiyadragon on 2006-07-21
Same problem here. Man, I'm having so many problems with my new pc. All hardware is detected, but so many problems. And all stuff that used to work just fine.

Now I have to reboot to Windows just to shutdown the computer :-/ Shutting it down before any os is loaded also turns off the usb devices. So the only way they don't turn off is if I shutdown from Linux. Almost as if Linux is explicitely telling them to stay on...

---

### Post by bryonhowley on 2006-07-22
Same thing on my pc shut down with XP the lights on my keyboard and mouse shut off with Ubuntu they stay on like the pc is in standby instead of power down.

---

### Post by Doovoo on 2006-07-25
So, has anyone had any luck with this? I'm wondering if it could have anything to do with the BIOS as well.

---

### Post by Paki on 2006-08-08
I haven't been able to figure anything out... In fact, I'm thinking of moving back to Breezy....

---

### Post by Madpilot on 2006-08-17
> **Paki said:**
> I have the same problem with USB devices staying powered. USB power is turned off when Windows shuts down the system, and USB power used to turn off when Ubuntu 5.10 was shutting down the system.

I notice that another linux distrobution gives me the same problem. It makes me wonder if the issue isn't in Linux kernel 2.6.15?

I've noticed the same problem with 6.06 - my mouse isn't shutting down like it did under XP, 5.04 & 5.10.

I've filed a bug with Ubuntu about it, but there's been no other comments or action since I filed.

If a few other people go [to the bug report]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-mouse/+bug/48773") and say "Me too!" we might get some notice.

I'm going to post a link to this thread from that bug report, as well.

---

### Post by greyghost60 on 2006-08-21
I found the answer, well in my case at least. I had a couple of dead USB
sticks (USB 1.1) attached to the machine. When I removed them everything
worked fine, Might be worth a check.

I am nor sure it was cos they were dead or cos they were 1.1.

---

### Post by Haiyadragon on 2006-09-28
Any luck with this? This needs more attention. It seems to be a problem with the new kernel. Shutting down from Linux (any distro so far) is the only way the devices stay powered. Any other way of shutting down will cut the power.

---

### Post by sultanoswing on 2006-09-28
Same here (Dapper)...I also had the same problem with Fedora Core 5. M/B is Gigabye K8NS (nforce3, skt 754). Mildy annoying.

...ho, and I filed a bug report at the link above too...

---

### Post by ironphil on 2006-10-04
It seems to be a problem with the kernel. I see that on every distro with kernel 2.6.15 and up. Maybe we should look on the kernel bugzilla to see if it is bug or a "feature".

---

### Post by ironphil on 2006-10-04
I just looked on the kernel bugzilla and it is report as bug #5410. It was first reported for kernel 2.6.13-rc2 so this is why there was no such problem for Ubuntu 5.10 which uses 2.6.12. 
Somebody wrote kernel 2.6.19 will probably fix the problem for some systems.
So yes, it is a kernel issue.

---

### Post by platinummonkey on 2006-10-24
Im having the same problem with both my saitek keyboard and logitech mouse as well as my logitech webcam. I think it might have something to do that all of these devices have "usb_device.can_wake_up" enabled, yet other usb devices that i have plugged in like my ipod, printer, flash drive, and a data collector do not have this feature enabled. Ive just started using ubuntu since last weekend, and i can locate teh file that i could possibly edit, yet it will not let me edit it even using sudo, possibly becuase these are kernal files? hmm, not sure, but maybe this might be of some help to someone?

---

### Post by 3rdalbum on 2006-10-25
I wish I was having this problem; it would be mighty handy for charging my mother's iPod.

---

### Post by Falchion on 2006-11-06
Having the same problem as everyone. Mouse and Keyboard doesn't shut off in Edgy like it does in the "Other" OS.

Agreed that it should be a problem with the Kernel as I didn't see this problem with Dapper. Then again, I am running a different Mboard then the one I had when I was running Dapper so it could be a issue only with certain Mainboards.

---

### Post by Muppeteer on 2006-12-14
Same problem here...Glad to see others are having this prob, thought there was some deeper evil at work :)

---

### Post by chrisccoulson on 2006-12-14
There is a bug report raised against the kernel [here]("http://bugzilla.kernel.org/show_bug.cgi?id=5410")

---

### Post by armalite on 2007-05-10
Oddly, usb proper shutdown when doing a suspend (to ram, to disk is unverified) on my pc. I have some little problems (lockup) in waking up my system but that's another thing :).

Why this does power off correctly when suspending and remains powered on when shutting down?

---

