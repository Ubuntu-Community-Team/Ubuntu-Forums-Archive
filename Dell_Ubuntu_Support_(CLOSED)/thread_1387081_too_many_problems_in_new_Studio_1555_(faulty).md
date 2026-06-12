---
title: "too many problems in new Studio 1555 (faulty?)"
date: 2010-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by v1nsai on 2010-01-21
I've had nothing but problems with my new Dell Studio 1555 since I got it about a month ago.  The system bricked after I installed a Dell BIOS update, and I'm not feeling too confident in Dell anymore.  After getting this thing fixed, I'm thinking of selling it.  Is anyone else with a Studio 1555 having problems like these?

Here's a little summary of some of the problems I've had
- I can't get the xserver-xorg-video-intel drivers to load.  I've used several distros and none of them will show the Intel graphics card as claimed when I 'lshw -C display'.  The video still runs ok, basic compiz effects lag though.
- I can't get the cd drive to burn or play any cds or dvds, burned or real.  Works in Windows.
- Screensaver never wants to come on, or turn the display off.  This may not be a hardware issue though.
- ACPI is b0rked.  The special 'fn' keys work for a while after restart, but eventually stop working until restarted again.  Can't adjust brightness at all after they stop working either.  I've tried booting with noapic, nolapic, acpi=force and various combinations of these but have had only marginal success where many have said these fixed the problem.

---

### Post by Darioff on 2010-02-01
Hi I was just about buying a new dell studio. does yours have the new i3 processor?
That's the one i was thinking about.

---

### Post by v1nsai on 2010-02-06
Turns out it was faulty, things have been much smoother with a new motherboard :-D

---

### Post by pythonsyntax on 2010-02-06
i was thinking of getting the same desktop but with a geforce card.

---

### Post by v1nsai on 2010-02-07
I bought a Dell thinking that since they were selling laptops with Ubuntu on them, that Ubuntu would run on it like it was made to run on it and have very few (if any) problems.  It still runs well, but has more than a few annoyances.

The cause of many of my problems has been ACPI, it just isn't working correctly, something to do with the embedded controller (EC).  This causes brightness and multimedia keys, detection of the lid being closed and the eject button to stop working.

tty usually doesn't render properly the first time I switch, I usually have to switch back to alt+ctrl+f7, then go back to alt+ctrl+whatever and it displays fine.  Also the Intel video drivers refuse to load, 'lshw -C display' still returns that both video interfaces are unclaimed, but video itself isn't bad at all I just had to disable a few compiz effects.  My screensaver never shows anything but a blank screen -_- I don't know if it's related to the xserver-xorg-video-intel driver or not.

I'm still pretty pissed about an update from the official Dell support site bricking my system (and how well known it was) and how long it took them to remove the driver from their website.  However I got a really good deal on my system and most of my problems are just annoyances, for the most part it works well and I'm very happy with it.

---

### Post by riksweeney on 2010-02-08
Apparently the lid issues are fixed in 10.04. Have you tried the latest driver from the ATI website?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

---

### Post by v1nsai on 2010-02-10
I'm using the Intel GMA card, I've read about there being a lot of problems with Linux and ATI, but Intel isn't working very well either >.<

---

