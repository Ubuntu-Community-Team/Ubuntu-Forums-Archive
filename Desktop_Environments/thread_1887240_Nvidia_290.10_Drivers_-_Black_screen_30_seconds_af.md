---
title: "Nvidia 290.10 Drivers - Black screen 30 seconds after boot"
date: 2011-11-26
forum: Desktop Environments
---

### Post by cxamer on 2011-11-26
I just upgraded the Nvidia Drivers on my media center computer running XBMC on Xubuntu 10.04.

The computer is a Acer R3600 Revo Intel Atom 330 2GB - NVIDIA Ion GPU

The driver is now at 290.10, System is booting normal and all seems well, but after about 30 seconds I get a mostly black screen, except for the top 5 CM of screen where I can see the GUI, when I move the mouse to the top of the screen you can see it move also. but the remaining 95 % of the screen is a pure black image.

Here is a picture of what I am talking about

[http://i.imgur.com/CcpVn.jpg](http://i.imgur.com/CcpVn.jpg)

Here is a pastebin of **/etc/X11/xorg.conf** [http://pastebin.com/aDU2WQgN](http://pastebin.com/aDU2WQgN)

---

### Post by stinkeye on 2011-11-27
Is xbmc set to autostart?

I'm using the Nvidia 290.10 Drivers with compiz on 11.10 Unity.
xbmc often becomes blacked out when I switch to windowed mode.
Switching back to fullscreen fixes it.(key above Enter).

If your using metacity may want to look at turning off/on the compositing feature
to see if it fixes the problem.
```
gconf-editor /apps/metacity/general/compositing_manager
```

---

