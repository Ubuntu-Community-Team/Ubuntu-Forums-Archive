---
title: "Desktop effects/compiz not working after nvidia driver install"
date: 2008-02-17
forum: Desktop Environments
---

### Post by mohnkern on 2008-02-17
Well I did something dumb, and I can't seem to back it out.

I'm running an Acer Aspire 9300 with an NVIDIA Geforce 7600 in it.  I installed Gutsy 64 bit, enabled the restricted drivers manager. Everything was working great except for every 30-40 seconds the screen would blink.

I went to Nvidia and downloaded the drivers and installed them.  That completely broke Gnome, So, I went to /etc/X11/Xorg.conf and changed the driver to "nv" and got things back to base line.

I re-installed the restricted drivers, and re-enabled them.  However, now when I go to Visual effects and select normal or extra, it tells me they can't be enabled, and when I type compiz from the terminal window I get:

mohnkern@scott-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


A tail from /var/log/Xorg.0.log shows:

mohnkern@scott-laptop:~$ tail /var/log/Xorg.0.log
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
(II) NVIDIA(0): Setting mode "1280x800"
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9


So the question is:

1) How do I get the desktop effects back and 2) This flashing I'm seeing, how do I get rid of it?

Thanks.

Scott

---

