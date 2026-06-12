---
title: "Windows can't be maximised from window panel"
date: 2012-10-03
forum: Desktop Environments
---

### Post by rkem on 2012-10-03
Hello!

[SOLVED this issue myself just now, but I'd still like to share it]

I am using Ubuntu 12.04 and encountered a strange issue - I've had this happen before with XFCE/Compiz and now with XFCE/xfwm4. 

1) I maximise any window to full-screen 
2) I minimise it to the window bar
3) I click on the icon/text representing the window (e.g. Firefox icon - Ubuntu Forums...)
4) The window doesn't maximise (or show up at all)
5) I try multiple times and the icon/text starts flashing, but it's not showing up on any of my workspaces

Even right-click -> unminimise doesn't make anything happen. It also doesn't matter if I send the window to any other workspace, it will never maximise/show up again. The only way to bring it back has been Alt-Tab.

I would be very thankful for any ideas/fixes regarding this issue. I don't see why a simple left-click with my mouse won't properly restore the maximised window.

[SOLVED] The Xfce window manager tweaks has a setting for "Activate Focus Stealing Prevention". For some reason, my left-click is seen as a focus steal...

---

