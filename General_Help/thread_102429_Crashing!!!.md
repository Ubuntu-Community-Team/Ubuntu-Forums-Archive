---
title: "Crashing!!!"
date: 2005-12-12
forum: General Help
---

### Post by katiad on 2005-12-12
Okay, so I have lots of crashing going on. X crashes, gaim crashes, firefox/thunderbird crashes, the KDE soundserver crashes... 

This doesn't seem like normal behavior. Also doesn't seem to be any particular rhyme or reason to the crashing. Sometimes it freezes up hard, requiring a forced reboot, sometimes not.

I know firefox is known to crash quite a lot, but.... X? Happens in both KDE & Gnome. And everything else, also?

I haven't really done much mucking around. This is the second install of ubuntu on this system (had a very badly failed upgrade, so I reinstalled from scratch) - and I had the same problems both times, so a random glitch doesn't seem likely.

What /would/ be a likely explanation? Hardware problem? Any way I could test that?

---

### Post by RAOF on 2005-12-12
Random crashing is infuriating, and difficult to diagnose.  Luckily, it's rare that something actually crashes truly **randomly**.  Most of the time there's some sort of trigger, even if it may be hard to work out what it is.  As for hardware testing, you can try running the memtest86 tests - just select the "memtest86" option from the grub boot menu.  That'll test your ram, at least.

General debugging hints:
* Running things from a terminal can be your friend.  Crashing stuff will usually spit out some form of debuging information before dying.
* Really important things leave logfiles behind.  Check out the X logs: /var/log/Xorg.0.log and their ilk.  Maybe they say something.
* The system log monitor will give you access to a lot of logs (auth, kernel, etc).  Maybe they will have some info.

After that, you could try compiling a kernel.  That's actually a reasonable stability test for the whole system - disc access, CPU, ram.

---

### Post by katiad on 2005-12-12
The error X gives each time it crashes is:
---------

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
SetClientVersion: 0 9

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by DrBair on 2005-12-12
Like RAOF said, I'd do memtest first. I usually allow it to run for 2 complete cycles before declaring memory to be good.  

What driver are you using for video?

---

### Post by katiad on 2005-12-27
Sorry for taking so long to reply here... Holiday hecticness, you know?

Anyway... does running memtest usually take FOREVER? I Set it to run one night when I went to bed. It was only approximately halfway through 8 hours later. Needed the computer, so I ended it and booted up... No errors noted or anything, but... extremely slow. I know I sat with it for a good 2 hours before I slept, and it was.... very very slow. 

As for the video driver - using the regular nvidia drivers...

---

### Post by RAOF on 2005-12-27
By "regular nvidia drivers" do you mean the (default) nv drivers, or the official closed-source drivers from nvidia?  You'll (probably) get a nvidia splash screen when you start X if you're using the official nvidia drivers.

If you're not using the closed-source drivers, try them.  Get the nvidia-glx package through synaptic, then run "sudo nvidia-glx-config enable" from a terminal.  I've had good luck with that fixing things in the past.

---

### Post by aysiu on 2005-12-28
One way to help diagnose where the problem lies--create a new user.

If the new user also has random crashing, it's a serious problem that's system-wide.

If not, then something's corrupted in your user profile.

---

