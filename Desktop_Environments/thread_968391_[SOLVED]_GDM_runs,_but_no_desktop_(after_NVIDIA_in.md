---
title: "[SOLVED] GDM runs, but no desktop (after NVIDIA install)"
date: 2008-11-02
forum: Desktop Environments
---

### Post by wizardStan on 2008-11-02
I just upgraded to 8.10.  The default video drivers were working very nicely, but I wanted 3D accel, of course.  So I went through the hardware thingy and had it install the restricted Nvidia drivers.  There were two, I went with the recommended one.
After download, install, and a restart, I no longer have a graphical login.  It just gives me tty1, text login.  I can swap through tty1-6, but my graphical login is gone.  The splash screen shows just fine.
A regular boot, text basically goes:

starting usplash...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/dis/by-uuid/.....) = dev..
kinit: trying to resume from /dev/disk/by-uuid/...
kinit: No resume image, doing normal boot...
Ubuntu 8.10 Stan-Desktop tty1
login:

So I do.  A process list shows that gdm is running.  "/etc/init.d/gdm restart" shows "Stopping GNOME Display Manager" followed by an extensive pause, and then "Starting GNOME Display Manager" as expected, with no apparent errors.  And yet, no change: I cannot get out of this text mode.
I have tried booting up in recovery mode, and running xfix.  In fact, I ran xfix, dpkg, and fsck just to be sure.  Still nothing.  When I resume normal boot from recovery mode, I do see it say "Starting GNOME Display Manager... [OK]" but it still drops me to text login.
As my last attempt at regaining control, I copied my failsafe xorg.conf file overtop of my existing one.  No dice, still text login.  With nothing left to try, I figured I'd just go back to default: dpkg-reconfigure xserver-xorg
NOTHING!  Still text login.  What am I doing wrong here?  What, short of another fresh install, will get me back to where I should be?
Rapid help would be greatly appreciated.

edit:
cat /var/log/Xorg.0.log
>>>
bunch of stuff, yadda yadda, loading pointer etc...
<the interesting part>
(!!) More than one possible primary device found
(--) PCI: (0@1:0:0) nVidia Corporation ... (bunch of numbers)
(--) PCI: (0@3:0:0) nVidia Corporation ... (more numbers)
<some more stuff about loading "extmod" and a bunch of extensions>
<load some modules successfully>
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
..... (driver information)
(II) Primary Device is: <note: nothing here.  Blank.  Nadda>
(WW) Falling back to old probe method for vesa
(EE) No devices detected.
Fata server error:
no screens found.


Yes, I have two video cards installed.  I SLI them when I boot into Windows to play games.  This did not cause any problems whatsoever in 8.04.  That seems to be causing the problem though: it can't decide which is primary, so chooses neither.  Does that make sense?  And is there a way to fix this?
Thanks!

---

### Post by Pro-reason on 2008-11-02
Perhaps you could try EnvyNG to install the right drivers.

Get to a console screen:

```

sudo apt-get install envyng-core envyng-gtk
sudo envyng -t
1

```

It may be necessary to mess around with /etc/X11/xorg.conf afterwards.

---

### Post by Pro-reason on 2008-11-02
Hmm, I've just read the bit about the two video cards.  Tricky.  Not sure about the correct config for that.

---

### Post by pirattrev on 2008-11-02
maybe it's something very stupid, like nautilus isn't running. that's my 2-cents

---

### Post by wizardStan on 2008-11-02
SUCCESS!
Having identified the problem as being due to two video cards, I did a little bit more research, and solved the problem by adding a "BusID" line to my xorg.conf file.
ie:
```
Section "Device"
  Identifier "Configured Video Device"
  Driver "nvidia"
  Option "NoLogo"
# Insert BusId here!
  BusId "1:0:0"
EndSection
```

So, I'm guessing the version of X shipping with 8.04 and earlier did something intelligent when encountering two cards: checking for connections, or simply picking the first one, or something.
Presumably the version of X shipping with 8.10 does not do this.  It sees two possible primary candidates, and gives up.  Telling it which one to use via BusId seems to be the only sensible work around.

---

