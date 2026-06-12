---
title: "evolution indicator missing"
date: 2011-07-09
forum: Desktop Environments
---

### Post by frogotronic on 2011-07-09
Hello,

Using Maverick.  Evolution indicator is missing when evolution is closed.  It's there when running (under the envelope).  How do I "reset" the behaviour?

Thanks,
CH

---

### Post by Frogs Hair on 2011-07-09
If Using  Classic Gnome you can right click the top panel select add to panel and add  the indicator applet . If the sound indicator still appears you may have another problem as it is part of the same applet .

To reset the panel applets to default , run this command in the terminal .```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

If you are using Unity the the applet is called indicator-messages and can found in the Synaptic Package Manager If it needs to be reinstalled for some reason.

---

