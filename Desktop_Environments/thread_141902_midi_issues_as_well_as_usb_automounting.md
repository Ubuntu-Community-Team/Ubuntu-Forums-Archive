---
title: "midi issues as well as usb automounting"
date: 2006-03-09
forum: Desktop Environments
---

### Post by blaine00 on 2006-03-09
These are KDE issues, but I am posting them here because they are most likely specific to Ubuntu with KDE as an add-on.

In Gnome as well as KDE, I am unable to play midis. The default program is KMid and when it opens, it gives me a message saying something on the lines of "dev/sequencer is in use. Could not open". I have no other audio programs running, and I am able to play other types of media. Is there something that could be using the sequencer in the background?

Also, KDE does not seem to automount usb devices... at all. If I start the computer with the device plugged in or if I plug the device in while already logged into KDE... it doesn't mount it. In Gnome, usb devices are mounted just as they are suppost to be.

Thank you everyone, in advance!

---

### Post by cwaldbieser on 2006-03-09
[QUOTE=blaine00]These are KDE issues, but I am posting them here because they are most likely specific to Ubuntu with KDE as an add-on.

In Gnome as well as KDE, I am unable to play midis. The default program is KMid and when it opens, it gives me a message saying something on the lines of "dev/sequencer is in use. Could not open". I have no other audio programs running, and I am able to play other types of media. Is there something that could be using the sequencer in the background?

Also, KDE does not seem to automount usb devices... at all. If I start the computer with the device plugged in or if I plug the device in while already logged into KDE... it doesn't mount it. In Gnome, usb devices are mounted just as they are suppost to be.

Thank you everyone, in advance![/QUOTE]
I have had off and on trouble getting kmid to work.  I found timidity to be much better.

As for the USB automounting in KDE, Kubuntu breezy uses ivman to manage that.  The man pages for ivman explain how it works-- I have never really played around with it too much myself, though I have seen plenty of articles in the forums reference it (especially in the Kubuntu forum).

---

