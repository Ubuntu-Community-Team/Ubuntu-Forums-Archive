---
title: "KlamAV failure"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by VoiceOvGod on 2007-07-11
I get KlamAV installed via synaptic no problem, however, when I try to run it, I get this:

```
~$ sudo klamav
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout
klamav: Checking for new ClamAV
klamav: ERROR: Couldn't start kio_uiserver from kio_uiserver.desktop: KDEInit could not launch 'kio_uiserver'.
klamav: Checking for new KlamAV
khtml (dom): WARNING: Can't communicate with cookiejar!
khtml (dom): WARNING: Can't communicate with cookiejar!
khtml (dom): WARNING: Can't communicate with cookiejar!
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)

```

Can I get a translation and help please?

And yes, I know I don't need an anti-virus :lolflag:

---

### Post by kitterma on 2007-07-12
Don't run sudo klamav.

Just run klamav.

---

### Post by gizmoarena on 2007-07-12
Does KlamAV fall under Desktop Customization? This is the wrong forum.

btw, if you are using ubuntu, you were supposed to install clamAV, not KlamAV.

---

### Post by VoiceOvGod on 2007-07-12
I just noticed that... yeah... don't know how it got in this one. oops.

---

### Post by VoiceOvGod on 2007-07-12
This has been moved to:

[http://ubuntuforums.org/showthread.php?t=499127](http://ubuntuforums.org/showthread.php?t=499127)

---

### Post by kitterma on 2007-07-12
> **gizmoarena said:**
> i...if you are using ubuntu, you were supposed to install clamAV, not KlamAV.

clamav is the anti-virus scanner.  klamav is the KDE gui for clamav.

---

