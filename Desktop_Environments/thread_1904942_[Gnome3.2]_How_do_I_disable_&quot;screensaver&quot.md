---
title: "[Gnome3.2] How do I disable &quot;screensaver&quot; by default"
date: 2012-01-05
forum: Desktop Environments
---

### Post by Spr0k3t on 2012-01-05
I've got a computer system I'm setting up to display random videos (from a script) on a screen.  The problem is, every 20 minutes the screen goes black and goes to sleep.  I've tried going into gnome system settings, then into screen... have the "turn off after" set to never, but it doesn't work.  Changing the turn off after to any other setting still turns off the display after 20 minutes.

Also, I checked to see if changing the information in dconf-editor would change anything, but no go.  org/gnome/settings-daemon/plugins/power/sleep-display-ac

---

### Post by santhony on 2012-01-07
I'm having the same issue as well... I'll let you know if I find anything...

---

### Post by Spr0k3t on 2012-01-13
I'm curious... what is your graphics chipset on your system with this problem?

```
*-display
     description: VGA compatible controller
     product: 2nd Generation Core Processor Family Integrated Graphics Controller
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 09
     width: 64 bits
     clock: 33MHz
     capabilities: msi pm vga_controller bus_master cap_list rom
     configuration: driver=i915 latency=0
     resources: irq:59 memory:fb400000-fb7fffff memory:d0000000-dfffffff ioport:f000(size=64)
```

Motherboard is the ASUS P8Z68-V

---

### Post by DGINSD on 2012-06-28
Just curious if any solution was found on your issue?  I'm having the same issue, though I rarely use gnome shell.

I've tried replacing gnome screensaver with xscreensaver, and I've tried completely removing both but all no joy.

I've tried the obvious as well setting to never, and changing settings in both gconf and dconf editors, still the screen times out.

I have a amd 64 chipset and am using the most current fglrx driver

---

### Post by amadness on 2012-06-28
go to Activities> System Tools> System Settings> Brightness and Lock.

---

### Post by kansasnoob on 2012-06-28
I've been using [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa") since Oneiric. I describe it very briefly in step #12 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

While that deals with classic/fallback I find Caffeine to work just as well in Unity. I have not tried it in a gnome-shell session.

---

