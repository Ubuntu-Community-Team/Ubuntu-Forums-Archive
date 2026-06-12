---
title: "Is there a sound applet in Xubuntu?"
date: 2016-06-17
forum: Desktop Environments
---

### Post by Evil Wayz on 2016-06-17
After a kernel upgrade broke Cinnamon, I switched to the lightest manager I could find that I liked.  I have xubuntu set up just the way I like it, except for one thing.  There's no sound applet that I can find.  I looked on the internet and read that the default sound apple was xcfe-mixer.  But when I try to install it, there is no such program.  I need it because one of my bluetooth headsets needs to be manually set to ad2p.

Using 16.04 with the generic 4.4 kernel.

---

### Post by Habitual on 2016-06-17
```
sudo apt-get install xfce4-mixer
```
and add that to the panel.

---

### Post by ajgreeny on 2016-06-17
Seems to have been removed from 16.04, but it was mainly, as far as I'm aware, just a GUI for alsamixer which is still available.
Why not use that.

Run alsamixer in terminal and set the levels of outputs.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

See [http://ubuntuforums.org/showthread.php?t=2322771](http://ubuntuforums.org/showthread.php?t=2322771)

---

### Post by Dennis N on 2016-06-17
I have indicator-sound in Xubuntu.

```
dmn@Sydney:~$ apt-cache show indicator-sound
Package: indicator-sound
Priority: extra
Section: sound
Installed-Size: 372
...
Filename: pool/main/i/indicator-sound/indicator-sound_12.10.2+16.04.20160406-0ubuntu1_amd64.deb
...
Description-en: System sound indicator.
 System sound indicator which provides easy control of the PulseAudio sound
 daemon.

```

xfce4-mixer is no longer used.

---

### Post by Evil Wayz on 2016-06-17
When I run that command, I get the following output:
```
wolf@shaitan:~$ apt-cache show indicator-sound
Package: indicator-sound
Priority: extra
Section: sound
Installed-Size: 372
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Conor Curran <conor.curran@canonical.com>
Architecture: amd64
Version: 12.10.2+16.04.20160406-0ubuntu1
Depends: libaccountsservice0 (>= 0.6.8), libc6 (>= 2.4), libgee-0.8-2 (>= 0.8.3), libglib2.0-0 (>= 2.37.3), libnotify4 (>= 0.7.0), libpulse-mainloop-glib0 (>= 0.99.1), libpulse0 (>= 0.99.1), liburl-dispatcher1 (>= 0.1), dconf-gsettings-backend | gsettings-backend, pulseaudio, gsettings-ubuntu-schemas (>= 0.0.1+14.04.20140224)
Recommends: unity-control-center | gnome-control-center | ubuntu-system-settings | pavucontrol | mate-media, accountsservice
Suggests: unity-greeter-session-broadcast
Filename: pool/main/i/indicator-sound/indicator-sound_12.10.2+16.04.20160406-0ubuntu1_amd64.deb
Size: 89178
MD5sum: 8d83a7fc7caffc8b0a6dfee03163cfba
SHA1: f45d9fedb80561005413b1b5b4c5cd5ce43bedfc
SHA256: df1f492d6fc36a086a1c891a07c5108e7ff7c07de64c72f945b045fadcc655d9
Description-en: System sound indicator.
 System sound indicator which provides easy control of the PulseAudio sound
 daemon.
Description-md5: fab6eabedadace061843b11db0e18547
Homepage: https://launchpad.net/indicator-sound
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, xubuntu-core, xubuntu-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntu-touch, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-mate-cloudtop

wolf@shaitan:~$ 

```

But when I try to create a launcher it doesn't work.

---

### Post by egeezer on 2016-06-17
Settings > Panel > Items > Add

---

### Post by Dennis N on 2016-06-17
Instead of a panel applet, Indicator-sound gives the volume control on your panel. Left click on the volume control and you get the sound menu. See the first screenshot. If you hover over the volume icon with the mouse, the mouse wheel will also adjust your volume (second screenshot).

Indicator sound should be installed by default with your Xubuntu 16.04 installation. If the volume control is missing, I'm not sure what it takes to correctly replace it. Maybe one of the experts here will have some idea on that.

---

### Post by ajgreeny on 2016-06-18
Right click in the panel, go to **Panel -> "Add new items" -> "Indicator plugin".**
That should do it, though I am also surprised that it was not there by default.

---

### Post by Dennis N on 2016-06-18
> **ajgreeny said:**
> Right click in the panel, go to **Panel -> "Add new items" -> "Indicator plugin".**
That should do it, though I am also surprised that it was not there by default.

It's part of the default Xubuntu 16.04 installation. So is indicator-sound. Makes me wonder possibly this is not really Xubuntu 16.04, but XFCE added to something. Other XFCE distros, like the Korora XFCE that I like, don't use the xfce4-indicator-plugin at all. Instead, it has a panel plug in for the sound.

---

### Post by egeezer on 2016-06-18
Ubuntu with the addition of xubuntu-desktop is a long way from Xubuntu - the mix leave Ubuntu in more control.  If you take Ubuntu and add xfce4 and xfce4-goodies, you get a more Xubuntu-like arrangement (used to do this a lot, until I switched to Xubuntu Core)

---

