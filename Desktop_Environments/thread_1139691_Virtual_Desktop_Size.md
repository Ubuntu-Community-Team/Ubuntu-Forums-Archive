---
title: "Virtual Desktop Size"
date: 2009-04-27
forum: Desktop Environments
---

### Post by chetancrasta on 2009-04-27
For the Linux gurus: Is there any way I can have a "virtual screen" that is larger than the actual resolution of my monitor? I used to be able to do this with RedHat linux sometime in 1998.
If you don't follow what I mean, have a look at this: [http://www.answers.com/topic/virtual-screen ]("http://www.answers.com/topic/virtual-screen")

---

### Post by zhocchao on 2009-04-27
if you are using jaunty: xrandr

---

### Post by chetancrasta on 2009-04-27
> **zhocchao said:**
> if you are using jaunty: xrandr

AFAIK, xrandr allows you to have a virtual screen but does not have the "mouse scrolling functionality". That is, it does not allow the user to scroll very large documents or multiple documents side by side by moving the mouse pointer beyond the edge of the screen.

---

### Post by zhocchao on 2009-04-27
jaunty -> xrandr

---

### Post by chetancrasta on 2009-04-28
> **zhocchao said:**
> jaunty -> xrandr

Could you give more info, please?

---

### Post by zhocchao on 2009-04-28
[http://ubuntuforums.org/showthread.php?t=1105594](http://ubuntuforums.org/showthread.php?t=1105594)

---

### Post by chetancrasta on 2009-04-28
> **zhocchao said:**
> [http://ubuntuforums.org/showthread.php?t=1105594](http://ubuntuforums.org/showthread.php?t=1105594)

Thanks for the info, zhocchao. It worked!
For anyone else reading this thread, here is the info:
With xrandr 1.3 and xorg-server 1.6 (included in Jaunty aka Ubuntu/Xubuntu/Kubuntu 9.04), you can have a large virtual resolution (it is referred to as "panning"). Here is the procedure to enable it:

Here are some examples:
```
Panning on a 1600x768 desktop while displaying 1024x768 mode on an output called VGA:
              xrandr  --fb  1600x768  --output  VGA  --mode 1024x768 --panning  1600x0

Panning on a 1600x768 desktop while displaying 1024x768 mode on an output called LVDS:
              xrandr  --fb  1600x768  --output  LVDS  --mode 1024x768 --panning 1600x0

Panning on a 2048x2048 desktop while displaying 1280x800 mode on an output called LVDS:
              xrandr  --fb  2048x2048  --output  LVDS  --mode 1280x800 --panning 2048x2048
```

If you get an error ```
xrandr: screen cannot be larger than 1280x1280  (desired size 2048x2048)
```
you need to edit your xorg.conf file.
Open a terminal window and type ```
sudo gedit /etc/X11/xorg.conf
```
Look for the section "Screen"
Add the sub-section "Display":
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual 2048 2048
	EndSubSection
EndSection
```
Save it and log out and log back in and run the xrandr command again.

That's it!

---

### Post by mkngl84 on 2013-02-16
This post is quite old but what I believe you are referring to is "Zooming" with Xorg or XFree86. The keys to use when activated are Ctrl-Alt-Plus/Minus. Apparently when KMS was introduced, that function was taken out or disabled. I found it useful for watching videos without scaling.

See this: [https://bugzilla.redhat.com/show_bug.cgi?id=631659](https://bugzilla.redhat.com/show_bug.cgi?id=631659)

---

