---
title: "Beryl on nc8430 (using flgrx)"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by NickDP on 2007-05-10
Hi,

I've been trying to get Beryl working on my laptop (HP nc8430) with Feisty (all updates installed). I've installed the prop drivers (flgrx), beryl, and xserver-xgl. I added a new session and everything seems fine but when I load the Xgl session I don't get the beryl splash screen - rather it looks like the plain X interface. Also, it appears that Beryl has crashed and reverted to standard Gnome session. My startxgl script is as follows:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

Could the problem be in this? I found a reference to "beryl-dbus" - should I be using this?

Any help would be great! 

Thanks!
Smilies
Nick

---

