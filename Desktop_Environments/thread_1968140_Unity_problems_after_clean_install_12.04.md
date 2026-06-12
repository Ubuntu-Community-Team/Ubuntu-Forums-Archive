---
title: "Unity problems after clean install 12.04"
date: 2012-04-28
forum: Desktop Environments
---

### Post by Paulgirardin on 2012-04-28
Initially everything was ok .I changed the wallpaper and made some minor changes to Unity with CCSM and Ubuntu Tweak.

Somewhere along the way the launcher icons have become low res (pixellated),
the dash does not respond to a super key tap or the HUD doesn't respond to a Alt key tap unless an app has a window open and window titles remain in the top panel after windows are closed.

Any tips to fix this?
I have tried unity --replace and unity --reset commands but they did not help.

Edit: This appears to be related to the installation of GLX Dock :if the dock is running all works ok,if I shut the dock down the misbehaviour starts.
Uninstalling the dock does not fix the problem though

---

### Post by Paulgirardin on 2012-05-03
bump

---

### Post by raashell on 2012-05-05
Sorry I can't offer any help in this, but I upgraded to 12.04 from 11 a few days ago and am having a similar issue in that if I tap the super key I get nothing unless a window is already open.  Similarly, upon startup some of the window names of applications show even though they're not actively open.

I'm running an Inspiron 15 Dell laptop from a couple years ago.  Potentially software conflicts might be Guake or TonidoSync, which both load on startup.  Additionally, I'm using xmodmap to flip my ctrl and alt keys and alter the location of the super key (though the super key still works normally-just the tap functionality doesn't work now.)

---

### Post by raashell on 2012-05-05
I disabled my startup applications and my xmodmap key changes and that didn't have any effect.

However, when I switched to Unity 2D, it works fine, so possibly this is something wrong with Compiz or my weak laptops ability to work with Compiz.

---

### Post by bohemian9485 on 2012-05-05
Compiz has its own key bindings and sometimes it conflict with the gnome key settings. I noticed that whenever I run glx-dock, I would lose my gnome keys functionality.

---

### Post by Paulgirardin on 2012-05-06
> **raashell said:**
> Sorry I can't offer any help in this, but I upgraded to 12.04 from 11 a few days ago and am having a similar issue in that if I tap the super key I get nothing unless a window is already open.  Similarly, upon startup some of the window names of applications show even though they're not actively open.

I'm running an Inspiron 15 Dell laptop from a couple years ago.  Potentially software conflicts might be Guake or TonidoSync, which both load on startup.  Additionally, I'm using xmodmap to flip my ctrl and alt keys and alter the location of the super key (though the super key still works normally-just the tap functionality doesn't work now.)

These are exactly the symptoms I am seeing.

---

