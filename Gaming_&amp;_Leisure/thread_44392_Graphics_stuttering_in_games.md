---
title: "Graphics stuttering in games"
date: 2005-06-25
forum: Gaming &amp; Leisure
---

### Post by skirkpatrick on 2005-06-25
Not sure if this belongs here or under hardware.

I had been running the 386 kernel with the NVidia driver and everything was fine.  I decided to upgrade to the 686 then K7 kernels and I noticed that both glxgears and Enemy Territory kind of stutters.  The motion is fine but stops briefly every few seconds.  Its' very regular but I'm not sure exactly how long.  I thought it was the new kernel but I can reboot and use the 386 kernel and it does the same thing.  Here's the results of cat /proc/driver/nvidia/agp/status:

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled


Anybody got any thoughts?

---

### Post by ltmon on 2005-06-25
No thoughts, but only to report the same thing happening to me :(

I also upgraded to the k7 kernel, but I didn't particularly notice that that was the point when the stuttering began.  I don't play enough 3d games to really know when it occurred.

L.

---

### Post by dolny on 2005-06-26
If you use KDE, try turning some kicker applets before playing. Try to kill kicker, launch the game and check if everything is ok. If you're running GNOME, check the process that suddenly increases the CPU usage. Maybe some GNOME tray applet?

Check it and post your results.

Try disabling FastWrites also.

---

### Post by skirkpatrick on 2005-06-26
FastWrites is disabled.  However, I think I do see the same problem when the screensaver kicks in.  I'll try disabling a couple of the gdesklets and see if one of them is causing the problem and report back here.

---

### Post by skirkpatrick on 2005-06-26
Ok, it's definitely a gdesklet.  In fact, it is the qstat desklets that are causing the problem.  I can bring up System->Preferences->Screensaver and watch the Preview pulse.  Disabling the qstat desklets stops the pulsing.

Even setting their update rate to 60 seconds seems to have no affect.  Guess it's time to sort through the code.

---

