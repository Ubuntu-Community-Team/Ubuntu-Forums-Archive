---
title: "Keyboard unresponsive after screensaver kicks in"
date: 2012-02-14
forum: Desktop Environments
---

### Post by Jiawen on 2012-02-14
If I let my 10.04 desktop stay idle long enough for the screensaver to kick in and the monitor to then go idle, the keyboard and mouse become unresponsive. As in, the only way to get the PC to respond is a hard reboot. I didn't have this problem with 8.04. It sounds like it might be related to [this bug]("http://ubuntuforums.org/showthread.php?t=1308494"), but I don't know how to check, nor if that's the right bug. What should I try? What can I fix?

---

### Post by papibe on 2012-02-14
What screensaver are you using?

Try testing something basic like 'Black Screen'. My first guess is that you are running a screen server that needs video hardware acceleration, OpenGL or something like that. If your computer don't support that, it maybe doing all the work with the CPU, thus the slowness.

Tell us how it goes.
Regards.

---

### Post by Jiawen on 2012-02-14
Thanks, I'll try blank screen.

I forget which specific screensavers I've tried. They're all the default Gnome ones, though. Most recently, the pictures folder one. Before that, I think I tried the Matrix one. Same results.

The system has an Nvidia 560 Ti card with the Nvidia drivers; it shouldn't be having any problem with video acceleration for a screensaver, should it? And the system isn't just slowing down; it's completely unresponsive to keyboard and mouse (number lock key doesn't respond, etc.).

---

### Post by Jiawen on 2012-02-15
> **reesepdt said:**
> If your computer don't support that, it maybe doing all the work with the CPU, thus the slowness.? I think I already addressed that.

---

### Post by Krytarik on 2012-02-15
> **Jiawen said:**
> And the system isn't just slowing down; it's completely unresponsive to keyboard and mouse (number lock key doesn't respond, etc.).
Try setting your "System -> Preferences -> Power Management" settings like in the attached screenshot; obviously, you can set the display sleep timer to any other value as well.

Hope that helps.

---

### Post by Jiawen on 2012-02-15
Will that prevent the screensaver from taking effect? 

Gosh, I've never thought to check the power management settings for a desktop. Thanks, I hope that works!

---

### Post by Krytarik on 2012-02-15
> **Jiawen said:**
> Will that prevent the screensaver from taking effect?
Nope, not at all; I have my screensaver running with exact those settings in the screenshot I've posted.

---

### Post by Jiawen on 2012-02-20
I finally got around to running an experiment with the new settings (leaving the monitor on with Cosmos screensaver going, sleep set to "never") and the system *still* froze. Keyboard unresponsive, mouse unresponsive, could only interact by hard resetting. What's causing this?

---

### Post by Krytarik on 2012-02-20
> **Jiawen said:**
> I finally got around to running an experiment with the new settings (leaving the monitor on with Cosmos screensaver going, sleep set to "never") and the system *still* froze. Keyboard unresponsive, mouse unresponsive, could only interact by hard resetting. What's causing this?
Maybe Gnome Screensaver just doesn't work nice with your specific system, that happens occasionally; I'd just try XScreenSaver instead (the guide is referring to Oneiric 11.10, but it should also work for Lucid 10.04):

[http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html](http://www.tuxgarage.com/2011/10/installing-xscreensaver-in-11-10-ubuntu.html)

---

### Post by Jiawen on 2012-02-21
There are some things I don't like about the Xscreensaver options as much as the Gnome screensavers, but that's just aesthetics. It seems to be working. Thanks! (I'm going to experiment for a few more days before marking it "solved", though.)

---

### Post by Jiawen on 2012-02-25
After a few days' experimentation, all seems to be working well. Thanks again!

---

### Post by Jiawen on 2012-02-27
Crud. I came home tonight to find that the X screensaver had frozen and that the mouse and keyboard were unresponsive. I had to hard reboot the computer. I thought this problem was solved, but now it appears that it's not! What can I do?

---

### Post by Krytarik on 2012-02-27
> **Jiawen said:**
> I came home tonight to find that the X screensaver had frozen and that the mouse and keyboard were unresponsive. I had to hard reboot the computer.
Now it really seems to be a graphics issue; what driver are you using for your Nvidia card, one offered by "Hardware Drivers"? If there is another driver available, I'd try those.

---

### Post by Jiawen on 2012-03-04
I'm using the Nvidia 295.20 driver. (The proprietary one, and the most current, so far as I can tell from [Nvidia's website]("http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html").) No other graphics drivers seem to be available.

Thank you for your continued help with this.

---

### Post by Krytarik on 2012-03-04
> **Jiawen said:**
> I'm using the Nvidia 295.20 driver. (The proprietary one, and the most current, so far as I can tell from [Nvidia's website]("http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html").) No other graphics drivers seem to be available.
Rechecking what Ubuntu version you are running - Lucid 10.04 - you are obviously using a driver provided by the [Ubuntu-X-Swat PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") or another PPA, or even installed it manually from Nvidia's website, since the latest version provided by the official repos is [195.36.24]("http://packages.ubuntu.com/lucid-updates/nvidia-current").

And yes, in Lucid 10.04, the "Experimental 3D support" I expected to be offered by the 'Jockey' driver manager (Hardware/Additional Drivers) is only available since Natty 11.04; and the "nvidia-173" seems not to be fitting your graphics device, otherwise it would be offered by the 'Jockey'.

So, what are your options now, as far as the proprietary Nvidia driver is concerned?: you could only try downgrading it to the version offered by the official repos of Lucid 10.04. Other than that, you could just disable the screensaver altogether, while leaving the display sleep feature activated - actually, I'm curious how this would work out; if that's affected, too.

---

### Post by Jiawen on 2012-03-09
> **Krytarik said:**
> Rechecking what Ubuntu version you are running - Lucid 10.04 - you are obviously using a driver provided by the [Ubuntu-X-Swat PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") or another PPA, or even installed it manually from Nvidia's website, since the latest version provided by the official repos is [195.36.24]("http://packages.ubuntu.com/lucid-updates/nvidia-current").I think I installed it directly from Nvidia's website, yes.
> So, what are your options now, as far as the proprietary Nvidia driver is concerned?: you could only try downgrading it to the version offered by the official repos of Lucid 10.04.I'd rather not downgrade, since I spent the money on this GPU and I'd like to get as much out of it as possible. I may just use the screensaver and be careful not to let the monitor go asleep with it on.> Other than that, you could just disable the screensaver altogether, while leaving the display sleep feature activated - actually, I'm curious how this would work out; if that's affected, too.Just to be clear, do you mean uninstalling Xscreensaver, or just setting it to "Mode: Disable Screen Saver"?

---

### Post by Krytarik on 2012-03-09
> **Jiawen said:**
> Just to be clear, do you mean uninstalling Xscreensaver, or just setting it to "Mode: Disable Screen Saver"?
Just disable it, yes - I'd just disable it in the "Startup Applications", so it isn't run in the first place.

---

### Post by Jiawen on 2012-03-10
> **Krytarik said:**
> Just disable it, yes - I'd just disable it in the "Startup Applications", so it isn't run in the first place.Okay, I'll try that. In the long term, however, I do want some kind of screensaver -- I want something to lock the screen when I'm away.

---

### Post by Jiawen on 2012-03-23
Turning off the screensaver while running xscreensaver still allows me to lock the screen. It'd be nice if I could find a true graphic screensaver that would play nice with my monitor setup, but for now, this does the job. Thank you again, Krytarik.

---

