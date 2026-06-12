---
title: "external storage doesn't appear"
date: 2010-11-20
forum: Desktop Environments
---

### Post by MichaelBurns on 2010-11-20
I'm using Xubuntu 10.04 live usb with persitence on a 4-GB MAXELL usb stick.  I "created" it using

Applications > System > Startup Disk Creator

from the Xubuntu 10.04 live cd.  From the cd, whenever I would plug in a usb device, it would appear in the

Places

menu unmounted but available (and also in the side pane? of Thunar?).  IMO, this is *ideal* behavior.  Unfortunately, this does not happen from the live usb.  Instead, I have to "manually" mount any usb devices that I plug in.  They appear as /dev files (e.g. from fdisk -l), but they don't appear conveniently in the file manager.  I have tried

Applications > Settings > Removable Drives and Media > Storage

for instance, but that only has to do with mounting.  It's not that the storage isn't mounting; it's that it doesn't even show up as a newly connected unmounted device in side panes, etc..  How can I fix it (so that the live usb behaves in this feature like the live cd)?

---

### Post by MichaelBurns on 2010-12-02
I guess I will try to explain this again.  Here is an update:

An ***un***mounted (but connected) USB stick does not appear in the "Places" menu (Xubuntu 10.04, xfce 4.6.1), nor in the side pane of the file browser (Thunar 1.0.1).  However, the same ***un***mounted USB stick then ***does*** appear in a pop-up download browser (Firefox 3.6.3).  Furthermore, once the USB stick is downloaded to, it is mounted (duh), and then subsequently appears in the "Places" menu and side pane of the file browser.  Alternatively, I have "no problem" to manually mount from the command line, I just want to figure out how to get thunar to handle this for me graphically.

I've tried the dummy methods: browsing through the setup menus and tinkering around for hours.

I've tried rerunning thunar as a demon :twisted:
```

nohup thunar --daemon &

```
(But, actually, this may be superfluous since thunar already appears in the output of ps -A.)

I've tried invoking the volume manager from cli:
```

thunar-volman --device-added '/org/freedesktop/Hal/devices/volume_uuid_BC2A_2F74'

```
(The udi was determined from the output of lshal.)

I've added the live user to the haldaemon group, which has apparently persisted, but doesn't help.

I am still very confused/baffled by the concept of installing a new file manager, window manager, desktop manager, etc..  And, frankly, from my google searching, that seems to lead to even more problems.  So, I'm hoping that there ***must be*** some simple stupid setting that I'm overlooking that somehow got changed when ripping the iso to the USB stick.  I reiterate that the behavior matches the CD when I boot for the first time from a freshly made live USB, but the behavior is changed in all subsequent boots.  (This phenomenon is repeatable; I started over 3 times - i.e. "Welcome to Linux").  This problem must be somewhere between HAL (which seems to be working properly) and Thunar (which also seems to be working properly otherwise).

What process/function/application/whatever am I missing between HAL and Thunar?

---

### Post by MichaelBurns on 2010-12-07
bump

(BTW, I'm back on Ubuntu Jaunty for the time being, but I hope to get my Xubuntu LTS issues sorted.)

---

