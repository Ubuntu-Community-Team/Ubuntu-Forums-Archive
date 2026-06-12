---
title: "Menu lag in XFCE w/ Compositing"
date: 2008-08-11
forum: Desktop Environments
---

### Post by valadil on 2008-08-11
I've been playing with XFCE 4.2 (or whatever the latest version is in the repositories) on my laptop.  It's great, but when I enable compositing my XFCE menu lags a lot.  When I click it or enter a new submenu, the menu opens but displays weird artifacts for a couple seconds before showing the actual menu.

There's a good chance this has something to do with the age of my laptop.  Compiz won't run on it (due to 16mb of vid memory instead of 64) so I was surprised XFCE's compositor ran at all.  I've noticed that once a menu has been opened, it doesn't go through the lag any more.  Is there any way to pre cache the contents of the menus so that I don't have to wait for them to load?  Or any other way to speed the menu rendering up?

Thanks.

---

### Post by x1a4 on 2008-08-11
Hi,
Setting the menu to 'Simple' instead of 'Multilevel' should help.

---

### Post by valadil on 2008-08-11
I think it was already set to simple.  I checked .config/xfce4/desktop/menu.xml and saw no mention of multilevel but there was a line that had simple in there.  Is there some other place I should look for changing that setting?  Alternatively is there a way to remove the icons from the menu?  I like them but wouldn't be surprised if they're a big source of the lag.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by x1a4 on 2008-08-12
The only other thing I was able to find is the compositor. The driver of your GPU is almost certainly not doing any acceleration, so composition is completely done on your cpu, which is probably already overloaded if this is an older machine. Disable the compositor and see if that helps.

---

### Post by valadil on 2008-08-12
It runs great without the compositor.  I was just hoping to get the machine running with compositing though.  

Are there any other options for configuring XFCE's compositor beyond what's in the settings window?  All I could find was settings for shadows and window decorations, but maybe theres some menu plugin that's slowing things down.

---

### Post by x1a4 on 2008-08-12
I *may* be able to help some more but first please answer some questions.

What's your video card and which driver are you using?
Are you using direct rendering?
Does the card use shared on-board video ram, and if so, is BIOS configured correctly to use the full amount of memory it supports? The menu artifacts are caused primarily by not having enough buffer memory available when using the compositor.

> **valadil said:**
> Are there any other options for configuring XFCE's compositor beyond what's in the settings window?
No.  Remember, Xfce is meant to be easy on resources.  Adding more features would undermine that.

---

### Post by valadil on 2008-08-12
--What's your video card and which driver are you using?
GeForce2 Go, w/16mb ram on the nvidia driver.

--Are you using direct rendering?
Not sure.  Is that DRI?

--Does the card use shared on-board video ram, and if so, is BIOS configured correctly to use the full amount of memory it supports? 
No, it does not use shared ram.

---

### Post by x1a4 on 2008-08-12
You may want to try a few tweaks, but from what I was able to learn, I don't think it's possible to run the latest version of Xfce smoothly with the compositing manager enabled on that particular piece of hardware. 

Still, give the following a try and see what happens.  These should help, but how much I don't know.

In /etc/X11/xorg.conf
```

Section "Device"
  ...
  Option         "DRI" "off"
  Option         "ShadowFB" "off"
  Option         "AddARGBGLXVisuals" "on"
  Option         "RenderAccel"  "on"
  Option         "AccelMethod"  "XAA"
  Option         "CIOverlay"    "on"
  ...
EndSection

Section "Screen"
  ...
  Option         "AllowGLXWithComposite" "on"
  Option         "AddARGBGLXVisuals" "on"
  Option         "SWCursor" "off"
  Option         "HWCursor" "on"
  ...
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection

```
Be sure to restart GDM when you're done
```
sudo /etc/init.d/gdm restart
```

---

