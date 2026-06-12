---
title: "broke my desktop..."
date: 2012-07-19
forum: Desktop Environments
---

### Post by jasonjob on 2012-07-19
Hello.  I'm using Ubuntu 12.04, with Gnome classic as my desktop manager, compiz as my window manager, and emerald as my window decorator.

All this was installed and working well, until...

I had the compiz settings manager open, and as I scrolled down the options via the mouse-wheel I managed to accidentally click the Ubuntu Unity Plugin (the one with the experimental section, not the one right down the bottom that has something to do with handles).

Things went wrong right from there.  The Unity dock intruded onto my desktop from the left, and my Gnome panel up the top vanished.  I was able to un-tick the plugin, but my computer locked up after that.

Upon re-boot, my Gnome classic session works, but I have no top panel (I DO, however, still have the buttons to make the top panel slide away for extra screen space), and my running applications no longer appear on the bottom bar (nor do my workspaces or the trash - but again the buttons to hide the bar are present).

Everything else seems to run as normal if I launch from the terminal.  Compiz is still working, as is Emerald.  compiz --replace and emerald --replace don't achieve anything (well, they both restart, but it fixes nothing, as they aren't what has broken).

Not sure just what has broken, but obviously the accidental attempt to utilise Unity inside Gnome-classic was something that should not have happened.

Any thoughts on how to fix this?  Wipe settings?  Re-install something?

Thanks

---

### Post by Version Dependency on 2012-07-19
Wait.  Do you have the Unity launcher and dash (hit the SUPER key) and all that stuff?  If so, then Unity Grab Handle plugin also required the Unity plugin to be selected.  So make sure to un-click both of those plugins and then log back in.

---

### Post by jasonjob on 2012-07-19
No, I greatly dislike Unity, which is why I was using Gnome-classic.  The problem seems to have come from accidentally turning Unity on inside Gnome-classic (until a few minutes ago, I did not realise that Unity was actually component of Compiz).  Unity functioned upon install, but I haven't seen it since then (about step three of my installation after OS and video driver was installing Gnome's interface).

So far as I recall, Unity Grab Handle has always been switched off (and I put it this way because I'm not at that computer at the moment so can't check, but I'm quite sure that it isn't selected).

---

### Post by Version Dependency on 2012-07-19
When you do a metacity --replace do you get your panels back?  Just trying to make sure the problem is with your Compiz settings.

---

### Post by jasonjob on 2012-07-19
Will try that when I get back home - but I was of the understanding that Metacity doesn't exist under Gnome 3.  I've read that it has been replaced by something called Mutter.

---

### Post by jasonjob on 2012-07-19
Okay.  metacity --replace gave me the default gnome decoration to my windows.  Did not restore my top panel.

Which seems to be there, kind of.  I've tried turning compiz settings on one by one (from a reset to defaults), and when I restored emerald as my window decorator, the shadow underneath the panel came back.  So there is something there, it just isn't visible or responsive.

---

### Post by jasonjob on 2012-07-19
Discovered that the panel is no longer changed by right-clicking, you <super><alt>-right-click.

So, having done that, I can restore the applets to the panel.  Sort of.  Can't restore the main menus as they were (there's just a ubuntu icon where there were two labels), and I cannot get applications to appear in the bottom bar.

Plus using the viewport switcher on the bottom panel now gives me a desktop without panels (even when I switch back to the first one), and compiz just gave me a seg-fault while searching for any and all mip-map options (already knew that they were broken).

So I can sort of get it working and looking like it was, but I'm not terribly satisfied, I still don't know just what happened (beyond the superficial "unity and gnome fought, and they both lost"), and I've this nagging feeling that my system is now unstable.

The odd thing is that I've just tried both a gnome 3 and a unity session, and both seem rock solid.

Anyone got any ideas short of an OS re-install?  And supposing I go that route, how do I ensure that my home folder survives intact?  I did it once a few years ago and can't recall the details :)

---

### Post by Version Dependency on 2012-07-19
Try resetting the gnome-panel to the default settings:

```
dconf reset -f /org/gnome/gnome-panel/ 
killall gnome-panel
```

---

