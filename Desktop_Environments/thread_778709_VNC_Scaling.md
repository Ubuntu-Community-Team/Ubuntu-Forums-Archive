---
title: "VNC Scaling"
date: 2008-05-02
forum: Desktop Environments
---

### Post by Derspankster on 2008-05-02
How can i scale the resolution of my VNC window? So far I've been able to configure to options, neither is totally acceptable to me.

I can log in at 640 X 480 vncviewer -fullscreen XXX.XXX.X.XXX:0 

This option doesn't give me actual full screen.

Secondly, I can add these two lines to my xorg.conf in the screens section of my host.

HorizSync 31-101
VertRefresh 60-160

Now when I log in I get a window that's actually larger than my desktop and I have to use the scrollbars to navigate. 

The machine I log onto is headless. I'd like a VNC window close to the 1280X1024 resolution of my monitor.

[B]Solved this with -fullscreen option.

vncviewer -fullscreen XXX.XXX.X.XXX:0  left HorizSync and VertRefresh lines in xorg.conf[/B]**[B]**[/B]

---

### Post by aliarnold on 2012-09-23
> **Derspankster said:**
> How can i scale the resolution of my VNC window? So far I've been able to configure to options, neither is totally acceptable to me.

I can log in at 640 X 480 vncviewer -fullscreen XXX.XXX.X.XXX:0 

This option doesn't give me actual full screen.

Secondly, I can add these two lines to my xorg.conf in the screens section of my host.

HorizSync 31-101
VertRefresh 60-160

Now when I log in I get a window that's actually larger than my desktop and I have to use the scrollbars to navigate. 

The machine I log onto is headless. I'd like a VNC window close to the 1280X1024 resolution of my monitor.

[B]Solved this with -fullscreen option.

vncviewer -fullscreen XXX.XXX.X.XXX:0  left HorizSync and VertRefresh lines in xorg.conf[/B]

please explain this way, i want when i change size of vncviwer window all content changing size too. 
How?
Thanx.

---

