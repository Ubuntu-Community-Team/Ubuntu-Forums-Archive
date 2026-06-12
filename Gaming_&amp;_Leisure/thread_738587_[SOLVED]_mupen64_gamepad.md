---
title: "[SOLVED] mupen64 gamepad"
date: 2008-03-28
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-28
Hi,
I recently installed mupen64.
I have a microsoft sidewinder gamepad. This is not recognised in mupen64.
Does anyone know how to get it to work?

I tried blights plugin - no luck.
Also I got this code, 
```
sudo ln -s /dev/input/js0 /dev/js0
```
but no good either

Thanks.

---

### Post by orethrius on 2008-03-28
What happens when you
```
cat /dev/input/js0
```
(ctrl + c aborts the test)?

Also,
```
dmesg | grep "SideWinder"
```
("SideWinder" may be "Sidewinder" or "sidewinder", try them all)

Just found this: [http://www.linuxcompatible.org/Microsoft_Sidewinder_Gamepad_Gameport_c9927.html](http://www.linuxcompatible.org/Microsoft_Sidewinder_Gamepad_Gameport_c9927.html)
```
sudo modprobe joydev; sudo modprobe gameport; sudo modprobe sidewinder;
```

Basically, you need to have the device recognised with appropriate drivers before the /dev subsystem can load it, then you can make the symlink with ln.  If the device is not loaded properly, neither of the first two codes will work.

---

### Post by Rytron on 2008-03-29
Hi,
I tried all of your code above, no luck.

The output for the sidewinder gamepad is jibberish

Which plugin should I use under options>configuration>plugins?
Mupen64 basic input plugin or blight's SDL input plugin 0.0.10

Also, my gamepad works perfect in all other emulators and games on ubuntu.

I can still control the N64 games with the keyboard, its not near as good as a gamepad though.

---

### Post by orethrius on 2008-03-30
Unfortunately, this is precisely why I use Nemu via Wine for N64 games.  I'm using a Logitech Wingman Rumblepad 2; Blight's doesn't handle the axes properly, and I've never seen any success with the basic input plugin.  You can work around it with some clever button reassignment, but I'm not sure that it can really be totally cured.

[quote=Rytron]The output for the sidewinder gamepad is jibberish[/quote]

It's a raw socket.  If it's NOT outputting gibberish, THEN there's a problem.  ;)

---

### Post by DoktorSeven on 2008-03-30
To be clear, in Blight's plugin, clicking the area beside Device: doesn't bring up (eventually) a Sidewinder Gamepad label?  I have a Sidewinder and except for having to blacklist the "analog" module at boot (add "blacklist analog" to /etc/modprobe.d/blacklist) to get the pad to work, it works just fine.

---

### Post by orethrius on 2008-03-31
> **DoktorSeven said:**
> To be clear, in Blight's plugin, clicking the area beside Device: doesn't bring up (eventually) a Sidewinder Gamepad label?  I have a Sidewinder and except for having to blacklist the "analog" module at boot (add "blacklist analog" to /etc/modprobe.d/blacklist) to get the pad to work, it works just fine.

Speaking of which, I just got a usable config for my Rumblepad in Mupen.  It's probably due to the updated Wingman drivers, but my axes weren't recognised until now.

---

### Post by acoustibop on 2008-03-31
AIR when I used a RumblePad 2 before with Blight's plugin in Mupen 64, it worked fairly much out of the box - I haven't had Mupen64 installed for a while, though.  Ubuntu will generally recognise a RumblePad 2 straight away - no problems.

A Microsoft Sidewinder and a Logitech RumblePad 2 are completely different controllers - different manufacturers, even.

---

### Post by orethrius on 2008-04-04
> **acoustibop said:**
> AIR when I used a RumblePad 2 before with Blight's plugin in Mupen 64, it worked fairly much out of the box - I haven't had Mupen64 installed for a while, though.  Ubuntu will generally recognise a RumblePad 2 straight away - no problems.

A Microsoft Sidewinder and a Logitech RumblePad 2 are completely different controllers - different manufacturers, even.

I get that, I just figured that my experiences might lend something of value to the subject. ;)

---

