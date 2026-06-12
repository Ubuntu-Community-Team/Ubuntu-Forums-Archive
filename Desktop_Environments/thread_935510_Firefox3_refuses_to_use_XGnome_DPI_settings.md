---
title: "Firefox3 refuses to use X/Gnome DPI settings"
date: 2008-10-01
forum: Desktop Environments
---

### Post by 757_Hokie on 2008-10-01
I've been looking all over and trying things out the last two days and can't get this working right.  Some background: I'm on a 15.4" laptop with a native resolution of 1920x1200.  Because of this, the default 96DPI in Ubuntu (and WinXP as well) is way too small for me to read stuff comfortably.

I've changed the Gnome DPI setting by doing: System->Preferences->Appearance->Fonts->Details and bumping the DPI from 96 to 120 (which is what I use in XP).  This did exactly what I wanted - all gnome applications/terminals/open office/etc have much easier to read fonts ... all except Firefox (v 3.0.3).  

Now the UI & menus in Firefox are at 120dpi, but the web pages themselves are continuing to render at the lower 96dpi.  I've tried setting layout.css.dpi = 0, -1, 120 - this does absolutely nothing.

Tried forcing Firefox to use larger fonts - sort of works but breaks the layout of a lot of pages plus the fonts are still 'thinner' than the real 120dpi ones.

My output of xdpyinfo | grep resolution reads 120x120 dots per inch, so that should confirm X is configured right.

What else can I try?  It's really frustrating to have *everything* else using the Gnome/X 120dpi settings yet Firefox, when rendering pages, doesn't.  

Thanks for any help.:)

---

### Post by darylb on 2009-02-19
This may be related to [this]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/201487") bug.

However as you stated changing the layout.css.dpi value in firefox made no difference.
I had the same experience (firefox 3.0.6).
I even restarted firefox but it still didn't make any difference.

---

