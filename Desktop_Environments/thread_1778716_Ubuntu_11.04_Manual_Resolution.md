---
title: "Ubuntu 11.04 Manual Resolution"
date: 2011-06-09
forum: Desktop Environments
---

### Post by quindraco on 2011-06-09
I use two monitors.  In the previous version of Ubuntu (I think 10.10?), both worked fine.  As of upgrading to 11.04, one monitor will only go up to 1024x768 resolution (I am shooting for 1280x1024).  This is the "Unknown" monitor; the other shows up as a Dell, which is accurate.

As Ubuntu clearly does not recognise the monitor, I am surprised that it does not seem to have a way for me to tell it about the monitor.  The list of available resolutions is a drop-down, with no interface for adding new ones.

How do I go about adding new options?  Things I have tried:

*I tried updating my video card driver, an ATI Radeon.  This made the right-hand monitor drop to 800x600 resolution and refuse to change, regardless of what I set the ATI CCC driver software to.
*I tried Xorg -conf, which simply failed with an error message.

---

### Post by MarkX on 2011-06-12
I have struggled with screen resolutions for many years now!
It's the same with every new release: They fix things that ain't broken and never fix this, the most basic of problems.
 
One should be able to set the resolution manually in a GUI. The excuse is that in times of yore too high a refresh rate could blow up a CRT. Clearly that's not a valid excuse anymore and anyone should be able to set their screen resolution manually. COME ON, CANONICAL!

---

### Post by bkratz on 2011-06-12
> **quindraco said:**
> I use two monitors.  In the previous version of Ubuntu (I think 10.10?), both worked fine.  As of upgrading to 11.04, one monitor will only go up to 1024x768 resolution (I am shooting for 1280x1024).  This is the "Unknown" monitor; the other shows up as a Dell, which is accurate.

As Ubuntu clearly does not recognise the monitor, I am surprised that it does not seem to have a way for me to tell it about the monitor.  The list of available resolutions is a drop-down, with no interface for adding new ones.

How do I go about adding new options?  Things I have tried:

*I tried updating my video card driver, an ATI Radeon.  This made the right-hand monitor drop to 800x600 resolution and refuse to change, regardless of what I set the ATI CCC driver software to.
*I tried Xorg -conf, which simply failed with an error message.

Post 8 of this thread helped much a lot.

[http://ubuntuforums.org/showthread.php?t=1769019](http://ubuntuforums.org/showthread.php?t=1769019)

---

### Post by MarkX on 2011-07-10
Tried using xrandr but using the cvt and gst tools creates the wrong numbers and my monitor goes into safe mode telling me to lower the speeds.
It seems that over the yaers of ignoring this problem, Ubuntu has lost users able to solve it.

---

### Post by mister_playboy on 2011-07-10
I am also having this problem.  I use my TV as a monitor and its resolution ( 1366x768 ) is not detected correctly.  Oddly enough, it was detected correctly in Ubuntu 10.10! :p

While following the process of adding a new resolution to xrandr did solve the problem, it's still very clunky.  Sometimes it boots up to the wrong resolution, even though I've added the correct one to my session startup.  Also, if I can switch the TV display off, I can't get back to the correct resolution from the Monitors GUI, I have to input the terminal commands.

I agree that this system needs to be correctly integrated with the GUI.. if the auto-magic detection doesn't work the first time, you have to suffer the consequences ever after... :(

---

### Post by MarkX on 2011-07-11
Tried uninstalling 11.04 and installing 10.04.2. STILL no joy adjusting the resolutions using the xrandr method. I get cvt to generate a modeline for 1280x1024 60 resolution but my monitor tells me its 1600x1024 and out of range. It seems almost like someone is SABOTAGING ways of manually setting resolutions in Ubuntu! WTF is going on????!!!!

---

