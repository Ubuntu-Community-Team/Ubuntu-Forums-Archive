---
title: "Unity launcher freezing"
date: 2011-09-16
forum: Desktop Environments
---

### Post by Sicadastra on 2011-09-16
I've just encountered this problem with my launcher. Weird enough, I'm not using too many programs (just 5: Firefox, Pidgin, Xpad, Evince and Tweetdeck) for it to act like that. If I point my mouse pointer at it, it won't pull back like it normally would after a few seconds. I also can't click on the icons and it's a bit upsetting since I use a shortcut for viewing several open windows on my desktop.

Is there a way to prevent it? Anyone who has encountered the same problem? :(

---

### Post by sikander3786 on 2011-09-16
Possibly, the graphics card or the driver is the culprit here. We need to see the output of this command from a Terminal:

```
sudo lshw -c video
```

---

### Post by Sicadastra on 2011-09-16
> **sikander3786 said:**
> Possibly, the graphics card or the driver is the culprit here. We need to see the output of this command from a Terminal:

```
sudo lshw -c video
```

It gave this output:

```
*-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f8100000-f81fffff memory:e0000000-efffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8200000-f82fffff

```

---

### Post by sikander3786 on 2011-09-16
Hmmm. It isn't what I expected to be the culprit.

You said the Launcher is freezing. Just making sure if the system itself is responsive, everything works except the Unity Launcher?

If yes, you can try updating your drivers via the "Xorg Edgers PPA" as mentioned here:

[http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)

If you later need to remove the drivers due to bad performance, you can install ppa-purge and purge all packages as mentioned on the same page.

---

### Post by Sicadastra on 2011-09-16
> **sikander3786 said:**
> Hmmm. It isn't what I expected to be the culprit.

You said the Launcher is freezing. Just making sure if the system itself is responsive, everything works except the Unity Launcher?

If yes, you can try updating your drivers via the "Xorg Edgers PPA" as mentioned here:

[http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)

If you later need to remove the drivers due to bad performance, you can install ppa-purge and purge all packages as mentioned on the same page.

Thanks! Hopefully it willwork :)

---

### Post by zx5000 on 2011-10-21
I'm having a similar problem except my whole desktop session freezes when I click the dash home button. I have to reboot the computer from a pseudo-terminal (ctrl-alt-f1). I tried killing whatever process had "dash" in it but it was still frozen.

Is there a way to use the old gnome interface?

```

me@mypc:~$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f4600000-f467ffff ioport:4000(size=8) memory:e0000000-efffffff memory:f4680000-f46bffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4700000-f477ffff

```

---

### Post by zx5000 on 2011-10-22
I did a complete re-install (backup, full format, selective restore) and eliminated the problem. There must have been some settings from the older versions that were incompatible with the upgrade.

Update: It did not fix the issue. Unity freezes my screen. My laptop can't handle unity.
Unity 2D does not lock up but I don't like it at all. It does not allow you to add your own menus or launchers. They just don't stick. And the icons are way too big. I'm old but not that old. 
Who thought it would be a good idea to emulate windows where the user has no control anymore?
 
Gnome-classic won't work with compiz and won't load as my default ~/.dmrc has no effect. Tried the removal of notifications as a requirement and no-go. It won't even go into classic that way.  

Very, very sad I updated. I will have to go back to 11.04.

---

