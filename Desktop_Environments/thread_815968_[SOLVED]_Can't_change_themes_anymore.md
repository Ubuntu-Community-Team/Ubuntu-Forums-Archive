---
title: "[SOLVED] Can't change themes anymore"
date: 2008-06-02
forum: Desktop Environments
---

### Post by DAC1138 on 2008-06-02
I was installing and playing with e17. I installed gtk-theme-switch2 to be able to change themes for root apps using gtk. Well, now that I'm back on XFCE, I can no longer change themes using the XFCE theme changing utility. Even with gtk-theme-switch2 uninstalled, it will not change themes.

So I reinstalled gtk-theme-switch2 and switched themes for the user. However, when I run gtk-switcher now as a normal user, themes dont change and I get a Segmentation Fault. But when I run it as root (via sudo) it changed the theme for all programs except those that run as root (like synaptic). So now when I need to change themes, I have to run gtk-theme-switcher2 as root, and even then it doesnt change themes for root apps.

I'm running Ubuntu hardy with all updates and XFCE version 4.4.2

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/gtk-theme-switch/+bug/78413](https://bugs.launchpad.net/ubuntu/+source/gtk-theme-switch/+bug/78413)

Has anyone found a solution? I just want to get it back the way it was, BEFORE gtk-switcher was installed. Where I could just go into XFCE or Gnome theme switcher and change themes WITHOUT gtk-theme-switcher.

---EDIT---
I've found a solution after further searching of the internet and forums: [http://ubuntuforums.org/showthread.php?t=411234](http://ubuntuforums.org/showthread.php?t=411234)

Pretty easy fix.

---

