---
title: "XFCE sanp to window wont disable."
date: 2012-11-27
forum: Desktop Environments
---

### Post by kidx on 2012-11-27
How can I stop the Snap to windows it wont disable at all.

---

### Post by LewisTM on 2012-11-27
You should provide a bit more details about what you are running and what you tried already.

On Xubuntu 12.10/Xfce 4.10, you can disable Window snapping in Settings Manager -> Window Manager -> Advanced -> Snap windows to other windows. Works perfectly here.

Cheers!

---

### Post by scottbomb on 2013-03-10
I'm going to bump this because this is my exact problem. I use two monitors, set up with an xandr script that runs on startup (shown below for reference, in case this has anything to do with it). My problem is that I cannot move a window from one workspace to another because as soon as it gets close to the screen edge, it "snaps" and resizes itself. A very annoying feature I don't want. I have window snap disabled in the Window Manager Advanced settings but it doesn't make any difference, they still insist on snapping.

By the way, this also happens on the laptop, using only it's one monitor. I can however move a window from one workspace to another but it still insists on snapping the window for me on top and bottom screen edges even though I have the feature turned off.

The script:

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
sleep 1
xrandr --addmode VGA-0 1280x1024_60.00
sleep 1
xrandr --output VGA-0 --mode 1280x1024_60.00 --pos 1920x312 --rotate normal --output DVI-0 --mode 1920x1080 --pos 0x0 --rotate normal --output HDMI-0 --off

---

### Post by Toz on 2013-03-11
Depending on the version of Xubuntu/Xfce that you are running, you may also have to disable "Window Manager Tweaks -> Accessibility -> Automatically tile windows when moving toward the screen edge".

---

### Post by scottbomb on 2013-03-14
Thank you Toz! That was it! This has been bothering me for about two years now and it's finally solved. It never occurred to me that there would be another setting that does basically the same thing. I changed that setting on the laptop and it's no longer "snapping". I can't try it on the big PC right now but I'll consider it fixed there too. Otherwise, I'll post back here tomorrow.

---

### Post by scottbomb on 2013-03-14
Well it fixed the problem on the laptop and it's no longer snapping on the desktop, however the desktop still won't let me move a window between workspace. I can right-click the title bar and select "move to another workspace" but I can't drag the window. I googled this problem and found answers related to compiz and unity but I'm not using either, just xfce.

---

### Post by LewisTM on 2013-03-14
To drag windows across workspaces, you have to enable it.
Check: Settings -> Window Manager -> Advanced -> Wrap workspaces when dragging a window off the screen.
Note that this automatically disables the aforementioned automatic tiling (although it doesn't uncheck it). So you can't have both.

---

### Post by 0£d$ko0l on 2014-03-06
Thank you so much for this. Although a year old thank god for these forums. I have hated the window snapping action on the fvwm window manager with such a passion. Figures its in one of the settings apps... but where?? I understand this is linux but we all could take a few ui lessons from Windows. Their UI stuff does work...

---

