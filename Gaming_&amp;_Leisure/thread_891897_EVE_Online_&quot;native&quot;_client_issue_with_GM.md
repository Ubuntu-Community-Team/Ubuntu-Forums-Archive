---
title: "EVE Online &quot;native&quot; client issue with GM965."
date: 2008-08-16
forum: Gaming &amp; Leisure
---

### Post by Rumplesmigskin on 2008-08-16
In b4 wine related.

Attempting to run EVE client on an Acer 2920 laptop - only splash screen comes up, and then the game dies. I'm just wondering if this is completely due to having a below-par video card (as it works on Windows no problem), or whether there is any way to mess with Cedega's settings so it will work.

Relevant info:
```
cpu: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
cpu_ghz: 1.33
memory: 2018
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
videocard_ram: 2048
agp_aperture_size: N/A
videocard_driver_version: 1.4 Mesa 7.0.3-rc2
soundcard: HDA Intel at 0xfc200000 irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-16-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066

```

Here's what the EVE client spits out before dying:
```
0005:  Bad stuff: client ignore setting select events for 0x90051f2c to 1
0005:  Bad stuff: client ignore setting select events for 0x90051f2c to 0
(above repeats about 40 times)
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3669
  Current serial number in output stream:  3671
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3676
  Current serial number in output stream:  3678
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  62 (X_CopyArea)
  Resource id in failed request:  0x3400350
  Serial number of failed request:  3677
  Current serial number in output stream:  3678

```

---

### Post by Lord C on 2008-09-15
Same problem here.

```
cpu: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
cpu_ghz: 2.0
memory: 984
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) Q35 20061017 x86/MMX/SSE2
videocard_ram: 1024
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 7.0.3-rc2
soundcard: HDA Intel at 0xfe9dc000 irq 1
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-21-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066
```

I get a whole load of;
```
0008:  Bad stuff: client ignore setting select events for 0x90058194 to 1
0008:  Bad stuff: client ignore setting select events for 0x90058194 to 0
```

Followed by;
```
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  146 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3565
  Current serial number in output stream:  3567
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  62 (X_CopyArea)
  Resource id in failed request:  0x380034e
  Serial number of failed request:  3568
  Current serial number in output stream:  3569

```

This is an intel onboard gfx card.

I tried the solution for intel chips, [on the cedega forums]("http://www.cedega.com/forum/viewtopic.php?t=9630"). Now the game launches, but I can't see anything.

[[IMG]http://img219.imageshack.us/img219/5519/screenshot1cn9.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshot1cn9.png)

And this error:
```
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  145 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x4c00005
  Serial number of failed request:  7007
  Current serial number in output stream:  7007
```

[Edit]
I've come to the conclusion that it is there Dells with their crappy onboard intel gfx cards, that are just not compatible with EVE.
I've tried to get EVE Classic to work in Windows XP, and the login screen constantly flashes. I give up  :/

---

