---
title: "Microsoft Wireless Mouse"
date: 2006-04-18
forum: Desktop Environments
---

### Post by DoodlesQ on 2006-04-18
Hi everyone. I just installed Ubuntu on my Dell laptop. So far so good. Got everything running no problem - searching these forums has been a great help. The one roadblock left is that I can't get my Microsoft Optical Wireless mouse working under Ubuntu. I still have winxp in dual boot, and it works fine there, so the hardware end is okay).

The device manager actually lists "Microsoft Wireless Optical Desktop 2.0" (which the mouse is actually a part of). However, the cursor is not moving or clicking at all. When the mouse is plugged in, I noticed the "microsoft wireless optical mouse" listing on the left pane of the device manager dissappears and reappears a lot. 

I can still use the laptop touchpad to move the cursor. I'm in USB, going through a HUB (though I tried it without the hub, same problem). I'd try PS/2, but I don't have any PS/2 ports.

Any googling or searching turns up people who can't get the mouse wheels or other buttons to work. Eitehr that or people reporting the mouse works fine. 

I had this problem originally in Breezy so I tried Dapper hoping that would somehow solve the problem. It didn't.

Thanks!

---

### Post by bikeboy on 2006-04-18
Seems strange, my dad's logitech wireless works fine so it's not the fact that it's a wireless mouse. As a laptop user I can offer one suggestion, does your laptop have a keyboard shortcut to turn off the touchpad? Perhaps it's defaulting to the touchpad and disabling the other mouse, if you turn it off the mouse may become active. Worth a shot anyway.

---

### Post by DoodlesQ on 2006-04-18
Doesn't look like there's a keyboard shortcut to do it. I tried doing it through xorg.conf, and while I succeeded in disabling the touchpad it still didn't help. Maybe somebody has a better way to disable the touchpad, but I don't think that's it.

---

### Post by bikeboy on 2006-04-19
Ok, try unplugging it, then plug it back in and type "dmesg | tail -10" at a terminal. See if there is anything at the bottom of that to indicate problems or otherwise.

---

### Post by GrumpyBob on 2006-04-19
Well, this isn't going to help, but if I am correct, I have one of these Microsoft mice - mine has a small grey transmitter that plugs in a USB port.  AFAIK, my mouse "just worked" as soon as I plugged it in to my IBM laptop.  Are other USB devices OK?

Robert

---

### Post by DoodlesQ on 2006-04-19
Other USB devices, including a hard drive and keyboard going through the same HUB, work perfectly. Bikeboy, I'll try your advice later when I get home.

---

### Post by kookookachooo on 2006-04-23
i have a microsoft wireless intellimouse, it works fine but i dont know how to configure my extra buttons. does anyone know how? thanks in adv.

---

### Post by TFrog on 2006-05-27
I too have been having issues with my Microsoft Wireless Optical Mouse 2.0 and Kubuntu.  It works most of the time on my desktop but has times when it randomly locks up the entire OS and forces a reboot :(  I read somewhere in the forums that it may or may not be a problem with udev.  All I know is for now I'm back to a wired mouse and Dapper LTS as of this writing.  Even the wired mouse froze up once in Dapper so it's most likely a problem with udev and I hope the coder's are working on that issue.

---

### Post by TFrog on 2006-08-07
Update on my last post.  I've tried various things and still get intermittent lockups.  I've tried both 386 and K7 kernels.  Also, I've removed the synaptics touch pad drivers and the wacom drivers just today.  We'll see if this stops the crap.  Also submitted a bug report about the issue.  Went through updating the XOrg mouse driver as well.  Keep your fingers crossed.

---

### Post by roachk71 on 2006-08-08
[LEFT]I have a USB Microsoft Wireless Desktop, and an extra wireless mouse from the same manufacturer. Almost the same problems (no hangs most of the time, but the mouse buttons frequently refuse to respond without moving the mouse.) The wireless keyboard works fine, as far as I can tell.

I wonder who else is having this kind of problem, with a possible fix. I'm tired of being locked down to the desktop by wires... :shock:

EDIT: Something I've noticed: Most of the time, after hibernation, I see several unsupported keycodes being passed through the USB root hub. My guess is that the mouse is also sending status information for the battery. Might this be useful?
[/LEFT]

---

