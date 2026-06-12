---
title: "A really easy compiz question ;-)"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by oldsmobile_mike on 2008-02-09
Hi!

Relatively new Ubuntu user here.  I've installed compiz and gotten it set up exactly how I want it with various effects, I've also installed the Yakuake terminal application (the one that drops down from the top of the screen, they call it "Quake-like").  Only thing is, I have compiz set up to have new windows use the unfold effect, but when I open Yakuake (F12) I want it to use a slide-down-from-the-top-of-the-screen effect, instead.  Any way to configure this in compiz, or get compiz to ignore the Yakuake window opening so it will slide down like it used to?  I've tried creating a seperate entry in compiz -> Animations -> Open Animation and setting the window match to "Yakuake", but this doesn't seem to have any effect.  Any suggestions?

Thanks!

---

### Post by psyopper on 2008-02-09
You are ont he right track with a seperate animation for the window. Take a look at the [Compiz-Fusion window matching]("http://wiki.compiz-fusion.org/WindowMatching") rules to see if you can get it sorted out...

---

### Post by oldsmobile_mike on 2008-02-09
> **psyopper said:**
> You are ont he right track with a seperate animation for the window. Take a look at the [Compiz-Fusion window matching]("http://wiki.compiz-fusion.org/WindowMatching") rules to see if you can get it sorted out...

Hummm...  it seems like what you're saying should work, but when I try any of the ways of identifying a window listed on that link I get the pointer crosshairs, but when I click on a window (any window, even a web browser window or other operating system window) I either get the response "atom", or "wm_name: no such atom on any window", or a blank response.  That guide mentions something called the "Regex Matching plug-in", but when I click on the link for that it directs to a blank page.  Any ideas?

Thanks!

Edit: I do have the compiz regex matching turned on, just saw it on the preferences screen...

---

### Post by psyopper on 2008-02-12
Try just using the xprop command without any of  the other stuff in the command, then click on a window.

---

