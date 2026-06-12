---
title: "Turning Off Monitors Kills Session"
date: 2017-11-24
forum: Desktop Environments
---

### Post by randall-lingenfelter on 2017-11-24
I've upgraded my Ubuntu Gnome 17.04 install to 17.10. I'm using the Gnome Xorg session and the issue I have is if I turn off my monitors, the session will die. If I power up my monitors again, I get the lock screen and I have to log in and all my programs I had open are gone. I've tried to stop screen locking under the privacy settings and I've been playing with gsettings variables, but nothing is fixing my issue. These are my gsettings right now:


gsettings get org.gnome.desktop.session idle-delay
uint32 0


gsettings get org.gnome.desktop.screensaver lock-enabled
false


gsettings get org.gnome.desktop.screensaver lock-delay
uint32 0


I'm using NVIDIA's 384.90 drivers to power two monitors that are connected via displayport (daisy-chained). This is the only issue I have and I don't want to wipe out my install just to fix this. This did not happen in 17.04. Any suggestions?

---

