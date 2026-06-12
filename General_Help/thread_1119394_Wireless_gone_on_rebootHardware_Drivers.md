---
title: "Wireless gone on reboot:Hardware Drivers"
date: 2009-04-07
forum: General Help
---

### Post by stim on 2009-04-07
I have two identical laptops with 8.10,just installed 8.10 yesterday on the second one.   The wireless was detected as proprietary and I was prompted to activate and restart, and my wireless was working well.  I shut down last night, restarted this morning and.... nothing.  Just vpn and auto eth0.

How can one machine work just fine and the other lose wireless after reboot.
The working computer detects the hardware as:

Broadcom Wireless STA Driver

Does anyone know how to force redection of hardware drivers, or have any insight into this?

I have been using ubuntu and have experience getting wireless to work since 6.06.I don't doubt that I can do it with ndiswrapper, I just dont understand why it worked and then stopped......

:mad:

---

### Post by stim on 2009-04-08
anyone?

---

### Post by mb_webguy on 2009-04-08
I had this same problem, caused by the latest update (though it was actually a fix that broke an existing work-around).

I had been using the Windows wireless driver for my Broadcom-based card, but the latest update included the STA driver.  Everything worked fine after I installed the proprietary driver (and actually considerably better than it did using the Windows driver), but after I rebooted the driver wasn't activated.

Apparently the driver should be -- but for some reason wasn't -- added to the /etc/modules file.  Open the file using "gksu gedit /etc/modules", and add "wl" (with no quotes) to the end of the file.

---

### Post by stim on 2009-04-08
Nice!
Thanks for the tip, I didn't think to check that.  I'm setting it up for someone and already gave it to them, (using vista until I have time to work on it :( ) so I will try this out tomorrow night.

Thanks again.

---

### Post by stim on 2009-04-09
```
sudo lsmod | grep wl
```

returned nothing, nor did 

```
sudo cat /etc/modules | grep wl
```

For whatever reason 
```
apt-get update
``` 
reported that linux-restricted-modules, linux-headers and linux-image were all "held back" on last update.  I did an

```
sudo aptitude dist-upgrade
```

Which I guess forced the updates through, now the module is loaded and the wifi is working.  Bothersome, even though it worked itself out, not something a complete n00b or novice would necessarily know how to do; especially confusing that it worked and then stopped.....

---

