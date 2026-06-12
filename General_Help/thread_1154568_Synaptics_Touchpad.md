---
title: "Synaptics Touchpad"
date: 2009-05-09
forum: General Help
---

### Post by m_2009 on 2009-05-09
Hi.

Is it possible to make my touchpad less sensitive.
For example if while I am typing my hand or thumb etc even brushes over the touchpad lightly, it will cause a click, or even click/drag etc.. This is very annoying as it can cause losing focus of windows etc..

In windows there are settings to change the amount of pressure that must be applied to the touchpad before it determins the action as a click or movin the cursor etc, and also settings to detect accidental brushing of the touchpad with the palm of your hand, which you can adjust the sensitivity of this detection too.

How can i set similar settings in Jaunty?
I know some people seem to use the xorg.conf file, however mine doesnt have a synaptics secion in here, and apparently things arent all handled in this file in Jauny anymore?

Could i do it with the fdi file /usr/share/hal/fdi/policies/20thirdparty/11-x11-synaptics.fdi

Any help would be appreciated.

---

### Post by spiderbatdad on 2009-05-09
I have not tried it, but there is a gui tool in synaptic package manager called "gsynaptics" for configuring the touchpad...also have a look at libsynaptics-dev & libsynaptics0
Apparently requires an entry in xorg.conf to work.

---

### Post by m_2009 on 2009-05-10
Thank you.

gsynaptics did the trick fo rme. There is a setting under tehre to allow adjusting how sensitive the touchpad is.

---

### Post by sgosnell on 2009-05-10
You can also get it through System/Preferences/Mouse.  I like touchfreeze, available in the repositories.  It lets you disable the touchpad while typing, using a specified delay time.  You can type without worrying about the touchpad, and it will stay disable for the specified time after the last keypress.  The default is .5 second, but I prefer 1 second.

---

