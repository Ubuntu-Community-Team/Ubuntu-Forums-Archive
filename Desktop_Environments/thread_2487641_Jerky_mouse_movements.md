---
title: "Jerky mouse movements"
date: 2023-06-11
forum: Desktop Environments
---

### Post by py-ohayo on 2023-06-11
Hello,

For the past 2-3 months, I've had some pretty annoying issues with mouse behavior: mouse handling becomes extremely difficult, e.g. when I try to drag the mouse cursor, nothing happens at first, then the cursor jumps to half the screen.
I searched on the web for a solution and didn't find more or less intelligible hint.
There are suggestions to do some actions based on result of xinput command.
I run it, but it seems that my mouse Logitech M187 isn't recognized.
```
pavel@MISSURI:~$ xinput --list --short
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:16                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:16                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:16                id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:16                        id=9    [slave  keyboard (3)]
pavel@MISSURI:~
```

I visited Logitech,
[https://www.drivers-logitech.com/logitech-m187-driver/](https://www.drivers-logitech.com/logitech-m187-driver/)
According to this page Logitech has no Linux driver for this mouse.
I worked with this mouse since at least 3 years ... and if my memory is good, the these mouse issues started to appear after upgrading to Ubuntu 22.04 (but I'm not sure at 100%).
Any suggestions ?
Thanks

---

### Post by Holger_Gehrke on 2023-06-11
Oh, it's recognized alright, but you're looking in the wrong place. xinput is meant for X11, with Wayland you'll only see a virtual representation of your pointing device and won't have any access to the underlying hardware. You could look at the output of 'lsusb', then you'll see that it is indeed recognized. Since I'm using XUbuntu and XFCE doesn't (yet) use Wayland I don't know how to diagnose this kind of trouble, but from what I've read Wayland goes for a GUI-tools first approach.

A search for "Wayland mouse lag" led me to this [bug report on launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1982560"). Might be something in there that could help you.

Holger

---

### Post by py-ohayo on 2023-06-18
Thanks. Indeed lsusb shows that mouse is recognized.
I looked through your link source. It seems that the solution is still not found.
What is strange with this phenomenon is that there are times when the mouse behaves correctly, then all of a sudden it comes.
For example, the last two days it was OK, and today the mouse is going crazy again.
If you are familiar with the lsusb command, can you please assess that everything is fine with my USB settings.
Thanks.

```
py@MISSURI:~$ lsusb
Bus 002 Device 004: ID 1058:25ed Western Digital Technologies, Inc. My Book 25ED
Bus 002 Device 006: ID 1058:25f6 Western Digital Technologies, Inc. My Book Duo 25F6
Bus 002 Device 005: ID 1058:25ee Western Digital Technologies, Inc. My Book 25EE
Bus 002 Device 003: ID 1058:25f9 Western Digital Technologies, Inc. ASM107U3
Bus 002 Device 002: ID 05e3:0617 Genesys Logic, Inc. USB3.0 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:210e Acer, Inc EasyCamera
Bus 001 Device 005: ID 1058:25f8 Western Digital Technologies, Inc. ASM107U2
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 8087:0a2a Intel Corp. Bluetooth wireless interface
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Holger_Gehrke on 2023-06-18
There's not much in terms of settings for USB connections, it really is plug-and-play.

I assume the mouse is connected through the 'Logitech, Inc. Unifying Receiver' - meaning it's a wireless Logitech mouse. You could get more information on that particular device using 'lsusb -v -d 046d:c534'. Since it's wireless and probably using a part of the spectrum that is filled with traffic by all kinds of devices, it might simply be interference by other devices which may or may not be under your control which would explain the intermittent nature of your problem ... Have you tried using a wired mouse to see whether that suffers the same problems ?

Holger

---

### Post by fyfe54 on 2023-06-19
Does the mouse need cleaned? Dust and detritus can make them act up.

---

### Post by him610 on 2023-06-19
There once was a Logitech M187 mouse. 
Sometimes mice die. This M187 fell to the floor and its tiny heart ceased to beat. 
It was solemnly buried it in the nearest trash can. 
All the peripherals chanted, "The mouse is dead, the mouse is dead." 
It was replaced by an available M317c. 
All the peripherals sang, "The mouse lives, the mouse lives." 
And they all lived happily ever after.

A true story that I witnessed.

---

### Post by ActionParsnip on 2023-06-20
If you switch to Xorg on the login page is it OK?

---

### Post by aljames2 on 2023-06-20
I had an older z77 motherboard where USB mouses (mice), were flaky if plugged in to a USB 3.0+ port, only happy in 2.0.  Probably not this but sharing anyhow.

---

