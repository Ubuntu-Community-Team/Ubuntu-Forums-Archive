---
title: "Panel deformation/decolorisation"
date: 2011-02-18
forum: Desktop Environments
---

### Post by Alpha_Bet on 2011-02-18
I am a happy ubuntu 10.10 64-bit user on my notebook.

The other day, i plugged my notebook to a projector to show some slides. Everything operated normally and shut down the system. 

When i turned on my notebook, my gnome panel had changed its appearance to this:

[http://bayimg.com/nAdPnaAdo](http://bayimg.com/nAdPnaAdo)

And yep, it's permanent. However, the problem is only visual. Everything works as usual.

Any ideas how to fix it??

Thanx

---

### Post by Krytarik on 2011-02-18
It seems like there is a background image set for this panel, right-click at it, choose "Properties", then "Background", and check what is selected there.

If that doesn't fix the issue, reset the panels by running these commands:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Alpha_Bet on 2011-02-19
> **Krytarik said:**
> It seems like there is a background image set for this panel, right-click at it, choose "Properties", then "Background", and check what is selected there.


That was it :shock:...

RESPECT and thanx Krytarik!!!

---

### Post by Krytarik on 2011-02-19
:popcorn::P

---

