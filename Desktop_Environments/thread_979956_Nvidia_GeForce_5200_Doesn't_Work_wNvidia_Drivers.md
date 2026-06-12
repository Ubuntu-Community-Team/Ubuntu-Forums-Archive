---
title: "Nvidia GeForce 5200 Doesn't Work w/Nvidia Drivers"
date: 2008-11-12
forum: Desktop Environments
---

### Post by sfarber53 on 2008-11-12
I'm running 8.10 with an Nvidia GeForce 5200 video card.  Before upgrading from 8.04 I had the same problem I am about to describe.

Without the Nvidia drivers I get a maximum screen resolution of 800x600.  With the Nvidia drivers I get a maximum screen resolution of 640x480. This is not acceptable to me.  I need a minimum screen resolution of 1024x768.

I've searched for a solution, tried having the system rewrite the xorg.conf file, but have had no success.  I've even tried editing the xorg.conf file manually.

I would really appreciate it if someone could help me out on this.

Steve F.
Blacklick, OH

AMD Athlon 64 3000+
1GB Ram
GeForce 5200 Video with 128MB Ram
Optiquest Q19wb LCD Monitor (17")

---

### Post by Eddie Wilson on 2008-11-12
Did you use the Nvidia Setting manager thats included in 8.10? Use it to set your resolution and freq. Don't use the other Screen Resolution app. It won't read correct.

---

### Post by sfarber53 on 2008-11-12
> **Eddie Wilson said:**
> Did you use the Nvidia Setting manager thats included in 8.10? Use it to set your resolution and freq. Don't use the other Screen Resolution app. It won't read correct.
Thanks, Eddie, but I couldn't get the utility to do anything.  It behaved erratically and wouldn't allow me to change any of the settings.

Any other ideas?

---

### Post by sloppyc on 2008-11-13
I read in some blog somewhere that the 5200 cards don't like the 177.xx nVidia drivers.  Try version 173.xx?

---

### Post by stinger30au on 2008-11-13
5200 only work with beta 76 drivers

---

### Post by strutzz on 2008-11-13
I had the same problem with a nv GeForce2 mx 400 and i just ran in terminal: sudo displayconfig-gtk , i selected my monitor and screen resolution and it worked. I didn't get to instal the restricted drivers yet but I'l try .

---

### Post by sfarber53 on 2008-11-13
> **stinger30au said:**
> 5200 only work with beta 76 drivers

Thanks stinger.  I couldn't find the beta 76 driver, but I did find a 71.x driver that I thought I'd try.  The problem is that the driver won't install unless I shutdown X and I don't know how to do that.

How can I manually stop and start the X server.  Sounds dumb, I know, but I'm not as good at the command line as I should be.

Many thanks,

Steve

---

### Post by sfarber53 on 2008-11-13
Thanks to everyone for their help.  I decided to give up on the 5200 and pick up an AGP slot GeForce 6200 w/ 256 MB Ram, etc. since that card will work with the current drivers.

Does anyone need a GeForce FX 5200?  I have 2 that I'm selling cheap.

Thanks again to all.

Regards,

Steve:guitar:

---

