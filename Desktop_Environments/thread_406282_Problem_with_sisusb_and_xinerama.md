---
title: "Problem with sisusb and xinerama"
date: 2007-04-10
forum: Desktop Environments
---

### Post by Unholy Moley on 2007-04-10
I have a laptop with a USB to VGA adapter that uses the sisusb driver. The graphics adapter doesn't support hardware acceleration, which should come as no surprise. I have a dual monitor system setup and everything works except one problem. Direct rendering does not work on both monitors with the sisusb driver. This was reported in Xorg.0.log:

(WW) I810(0): Direct rendering is not supported when Xinerama is enabled
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.

With xinerama off, DRI will work on the primary monitor as it should, but without xinerama I can't move windows across screens, have a shared desktop, etc. What can I do to fix this problem? Is there perhaps an alternative to xinerama?

---

### Post by aqualad on 2007-04-10
Good call, I just realized it was doing this.  I ran glxgears and I got awesome results on the Left monitor, but sadly the fps dropped to crap on the right screen.  Let's hope for a fix soon :]

---

### Post by Unholy Moley on 2007-04-11
You misunderstood my post. DRI doesn't work on BOTH monitors with my usb2vga adapter installed and xinerama on.

---

