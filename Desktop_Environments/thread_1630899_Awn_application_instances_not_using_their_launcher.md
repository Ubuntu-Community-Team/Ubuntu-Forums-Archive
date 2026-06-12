---
title: "Awn application instances not using their launchers"
date: 2010-11-25
forum: Desktop Environments
---

### Post by SaintBasil on 2010-11-25
I have an issue with Awn. I have two custom launchers, for MATLAB 2010b and Mathematica 7, which misbehave. Rather than use the initial launcher to "host" each instance, they create new launchers for even the first instance. At first, I thought this was because the launcher name, e.g. MATLAB, did not perfectly coincide with the instance's name, e.g. MATLAB r2010b. After giving the launchers the same names as the new instances, they still refused to land on the initial launchers. With MATLAB, I can see that the splash screen does indeed use the custom launcher, but the actual MATLAB doesn't. Could it have something to do with the fact that I don't have the two programs in my PATH? Or is this a bug with Awn?

---

### Post by moonbeam on 2010-11-25
Try setting the StartupWMClass field value in the custom desktop file(s). [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

You can determine the value you want by running xprop on the application windows, look for WM_CLASS(STRING)

---

