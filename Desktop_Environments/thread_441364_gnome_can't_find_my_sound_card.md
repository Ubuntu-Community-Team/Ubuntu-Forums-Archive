---
title: "gnome can't find my sound card"
date: 2007-05-12
forum: Desktop Environments
---

### Post by bittergourd on 2007-05-12
I am pretty sure my sound card is fine, because
1. Players make sounds properly.

2. aplay -l:
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

3. And I can change the volume in alsamixer.

But, when gnome is loaded, it says can't open mixer applet (the thing in the sys tray).  In prefereces->sound, none of the playback finds any device at all.

It looks to me that the driver is properly installed, but the settings for gnome is screwed.  Actually for a while it fixed itself (I don't remember I did anything...), but now it doesn't work again.  The same thing happens to recycle bin as well: can't load applet, no recycle icon etc.  And, the two problems' working status have perfect correlation...

Can anyone help me on that one?  Thx!!

-E

---

