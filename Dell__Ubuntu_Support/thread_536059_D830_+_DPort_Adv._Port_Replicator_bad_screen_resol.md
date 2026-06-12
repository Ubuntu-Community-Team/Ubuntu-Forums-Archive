---
title: "D830 + D/Port Adv. Port Replicator: bad screen resolution?"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by christian.convey on 2007-08-27
Anyone seen this before?

I've got a Dell Latitude 830, plugged into a Dell D/Port Advanced Port Replicator.  

My external monitor is a Samsung SyncMaster 244T, with native resolution 1920x1200.  My laptop has an Intel G965 chipset, X3100 graphics (which supports 1920x1200), and a laptop screen resolution of 1280x800.

I'm running a pretty vanilla installation of Feisty (7.04).  I have installed the package xserver-xorg-video-intel.

When I use a VGA cable to connect my laptop to the monitor either directly, or indirectly via the port replicator, I can get 1900x1200 resolution.

But when I use a DVI cable to connect the port replicator to the monitor, I can only top out at 1280x864 screen resolution.

I've tried restarting X, running "dpkg-reconfigure xerver-xorg" and telling it that 1920x1200 is a valid resolution, etc.  Nothing seems to work.

Any suggestions?

Thanks,
Christian

---

### Post by bimbo on 2007-09-04
You need to mess with Virtual modes to get this to work.

Something along the lines of ```

Section "Screen"
        Identifier      "virtualscreen"
        Device          "i965gm-int"
        Monitor         "generic"
        Option          "monitor-LVDS"  "LCD"
        Option          "monitor-TMDS"   "DVI"
        DefaultDepth    24
        SubSection "Display"
                Virtual SUM_OF_HORIZONTAL_PIXEL MAX_VERTICAL_PIXEL
        EndSubSection
EndSection
```
courtesy of [http://www.linuxforen.de/forums/showthread.php?t=239217](http://www.linuxforen.de/forums/showthread.php?t=239217) (in German) in xorg.conf might help.

Or upgrade to Gutsy (which is still buggy, so be warned) and read into xrandr 1.2 docs for how LVDS/CRT/TMDS things work.

I can confirm that the DVI port can do at least 1600x1200 (but unfortunately I nuked the configuration that did this) so there's hope for sure.

---

### Post by christian.convey on 2007-09-04
Thanks!  I'll give it a shot once Gutsy matures a little more.  I'm running all my important stuff in VMWare.  So I can just back-up those virtual machines, and change Feisty to Gutsy underneath, hopefully.

---

### Post by neptho on 2007-09-04
> **christian.convey said:**
> Thanks!  I'll give it a shot once Gutsy matures a little more.  I'm running all my important stuff in VMWare.  So I can just back-up those virtual machines, and change Feisty to Gutsy underneath, hopefully.

Make sure you back them up to another medium, just in case if you need a reinstall.  Using a virtualized OS within an unstable OS and assuming that your data will be secure is very risky.  ;)

---

