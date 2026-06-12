---
title: "Upgrading NVidia drivers to anything higher than 331.38 breaks multi-monitor setup"
date: 2014-09-26
forum: Desktop Environments
---

### Post by pkolaczk-u on 2014-09-26
I upgraded nvidia drivers to 331.89 (and also tried 340.32 and even some 342.x) and the effect is always the same - when working on single, built-in laptop monitor (FHD) everything looks fine. When I connect a second monitor to DP (2560x1600), the login screen looks ok, but after logging into my account, the desktop is completely distorted and unusable. It looks as if the system thought the total screen width in pixels was much smaller than it really was (1920 + 2560) and draws the wallpaper and windows stretched horizontally. Funny, unity launcher and the top status bar are drawn correctly, and clicking on the icons in the launcher even launches apps. Therefore I think this looks more like a Unity/Compiz bug, not Nvidia problem. 

I tried cleaning .config/compiz-1 and .compiz directories, as well as deleting /etc/X11/xorg.conf, but with no luck. Also the issue seems extremely repeatable - I plug the second monitor in - desktop distorted, I unplug it, desktop ok, plug it in - again distorted. 

The problem disappears permanently once nvidia downgraded back to the officially supported 331.38. 

Anyone already ran into this? Is Ubuntu 14.10 going to have a newer, tested nvidia driver but without the issues I described above?
I was hoping the upgrade improves performance on multi-monitor setup, the current driver version feels sometimes laggy. 

Also - are there any plans to support DisplayPort through the builtin Intel GPU on laptops where DP is permanently attached to Nvidia card? Windows seems to support it via some virtual screen cloning (I guess it renders everything on Intel GPU and copies to Nvidia card to make it available through DP). Or at least making GPU switching more intelligent, so it could detect DP is connected and switch to Nvidia automatically? Currently whenever I want to use external monitor, I need to log-in, switch Prime profile, log-out and log-in. And then do it again whenever I take my laptop with me, in order to save battery. 

I'm using Ubuntu 14.04. 
Hardware: Dell M4600, Nvidia Quadro 1000M, Sandy Bridge i7 Core Quad @2.4 GHz, 24 GB RAM.

---

