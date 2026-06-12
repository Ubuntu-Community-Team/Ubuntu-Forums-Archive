---
title: "Compaq Presario freeze"
date: 2009-02-26
forum: General Help
---

### Post by dwiedenfeld on 2009-02-26
My Compaq Presario F500 freezes solid at random intervals, from < 1 minute to several hours after boot up. It just absolutely stops--no cursor movement, nothing moves. Only thing to do is hold down the power button until it goes off and then reboot. This does not seem to be related to Firefox (my first suspicion) or to OpenOffice (my second). Right now I'm suspicious of the Invidia drivers. 
Here's the specs:

Compaq Presario F500
AMD Turion 64 processor
Ubuntu 8.04 LTS Hardy Heron
Broadcom wireless
Nvidia graphics

One question: I did not install the 64-bit version of Ubuntu--it's running the "regular" 32-bit version. Might that be the problem? Or any other ideas? This problem makes the machine too unreliable to be usable.

Oh--and Compiz is turned off.

---

### Post by evilGUI on 2009-02-26
This could be one of many, many things, the most common are Wireless and Video related issues, for one you might try using the Vesa driver to see if it's a Video related issue, you can do this by simply editing xorg.conf and replacing Nvidia with Vesa. Also, do you use ndiswrapper with your Broadcom wireless? If so, this could be a kernel stack issue. Please give us more detailed information on your hardware, and which drivers you are using.

---

### Post by dwiedenfeld on 2009-02-27
> you can do this by simply editing xorg.conf and replacing Nvidia with Vesa.

Is it really that easy? I will try it.

> Also, do you use ndiswrapper with your Broadcom wireless?

Yes, I am using ndiswrapper. It is the only way I was able to get the wireless working on this machine. (Getting the wireless working was a pain.) This is also the reason I'm not terribly anxious to do a clean install or upgrade to Intrepid--worried that I might never get the wireless back.

By the way, I'm pretty much a newbie with Linux. I've seen (and probably even cookbooked it before--don't remember) how to get a list of the drivers, but I don't remember how. Any help on that?

---

### Post by dwiedenfeld on 2009-02-27
OK--I replaced "nvidia" with "Vesa" in my xorg.conf, and rebooted. Now I've got a display, but it's 800x600 and in "Preferences > Screen Resolution" that and 640x480 are the only choices. How do I get a higher resolution?

Oh, and isn't there a way to restart Xorg without having to reboot? Or not?

---

### Post by dwiedenfeld on 2009-02-27
Bump.

---

