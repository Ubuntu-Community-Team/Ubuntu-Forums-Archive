---
title: "X running slow in metacity - sometimes..."
date: 2007-07-16
forum: Desktop Environments
---

### Post by richardq on 2007-07-16
I'm running metacity on Feisty. I've got a i915 integrated graphics card and have the xserver-xorg-video-intel package installed and I'm having some trouble.

At least half of the time, when my system starts, I get slow scrolling in Firefox and Epiphany, and some visible artificacts when I drag windows around the desktop. Processing speed (of non-graphical things) seems unaffected.

I know when things will be slow, because I notice the spinning disc cursor (Is that what it's even called??) flashing slightly when programs are loading. It almost reminds me of a hard drive access light in that it just dims out intermittently when it's launching a program.

The times when the gui runs full speed I don't see this flashing of the cursor and everything runs top notch.

Any idea how I could figure out what was causing this? I'm not sure which logs to look at. I'm thinking it might be an incorrectly loading driver or some app behind the scenes slowing things down. 

Ctrl-Alt-Backspace doesn't always fix the problem. Nor does rebooting. It really seems random. 

The only other thing I notice is that the bootup sequence sometimes stalls for 2 minutes at the hald stage. Other times it flys right through this portion. I'm not sure if they're related and I'm not sure where to check why this is happening either.

Any help would be much appreciated.

---

### Post by richardq on 2007-07-17
Okay.. I figured out that I should look at the /var/log/Xorg.0.log files. I saved a copy of the log file on a 'slow' run and on a 'fast' run. Below I've shown the diff output between the two. While memory allocation addresses should likely differ in some way, the drmOpenDevice failures on the 'slow' run indicate that they might be the likely culprit. I think this shows me that on the slow runs the i915 card is not recognized or the i915 driver is not loading.

Anyone know what these messages mean and how to prevent them?

ps - the slow run is the 6:08am file

```
14c14
< (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 17 06:37:15 2007
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 17 06:08:38 2007
581,585c581,585
< (II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x13d75000 physical)
< (II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x1657c000 physical)
< (II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x12d7d000 physical)
< (II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x16574000 physical)
< (II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x15a34000 physical)
---
> (II) intel(0): 0x007bf000-0x007bffff: Core cursor (4 kB, 0x36c92000 physical)
> (II) intel(0): 0x007c0000-0x007c3fff: ARGB cursor (16 kB, 0x36124000 physical)
> (II) intel(0): 0x007c4000-0x007c4fff: Core cursor (4 kB, 0x36d99000 physical)
> (II) intel(0): 0x007c5000-0x007c8fff: ARGB cursor (16 kB, 0x36128000 physical)
> (II) intel(0): 0x007c9000-0x007c9fff: overlay registers (4 kB, 0x36043000 physical)
596c596,598
< drmOpenDevice: open result is 8, (OK)
---
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: Open failed
598c600,602
< drmOpenDevice: open result is 8, (OK)
---
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: Open failed
603a608
> (II) intel(0): [drm] loaded kernel module for "i915" driver
607c612
< (II) intel(0): [drm] mapped SAREA 0xf8d91000 to 0xb7e46000
---
> (II) intel(0): [drm] mapped SAREA 0xf8d91000 to 0xb7e63000
```

---

### Post by Diabolis on 2007-08-16
I had slow performance. My problem was that I didn't have the correct driver configured in my xorg file and I didn't have direct rendering.

this will tell you if you have it or not:
```
glxinfo | grep rendering
```

type this to go over your xorg file:
```
sudo gedit /etc/X11/xorg.conf
```

In the section called device I just change the driver to "i810" and it worked.

---

