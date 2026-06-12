---
title: "App switcher crashes in Compiz"
date: 2009-02-28
forum: Desktop Environments
---

### Post by spencercarran on 2009-02-28
I'm running Ubuntu 8.10 64-bit.

When I'm using Metacity (the default WM for GNOME) and I have visual effects set to "normal" or "extra," alt-tab produces, respectively, the same effect as Compiz's "Static Application Switcher" and "Application Switcher" while in "extra" super-tab produces the same effect as the Compiz shift switcher. All of these effects work just fine in Metacity, but when I use Compiz and I try to use any of these application switchers, my computer will freeze if any of my windows happens to be minimized. (It actually happened just now, as I was typing the previous sentence, a hard reboot followed and FF managed to restore my previous session). When this happens, Ctrl+alt+backspace does not get me back to a login screen, and ctrl+alt+f1 does not get me a console.

Has anyone else run into a similar problem? Does anyone know of a workaround?

---

### Post by spencercarran on 2009-03-08
Bump.

Has anyone run into the same issue? I can't think of anything special I've done that would have broken Compiz.

---

### Post by spencercarran on 2009-03-09
After some trial and error, it seems to be the Reflection plugin that is causing the problem. Can anyone confirm? (Enable the Reflection plugin, minimize at least one window, and try to use any of the various application switchers)

---

### Post by ehicham on 2009-03-13
> **spencercarran said:**
> After some trial and error, it seems to be the Reflection plugin that is causing the problem. Can anyone confirm? (Enable the Reflection plugin, minimize at least one window, and try to use any of the various application switchers)

Seem you are right. I started having the same problem once I have activated the Reflection plugin. after several crashes and reading your post. I desactivated it... and everything went back to normal.

thx for the hints...
Hicham

---

