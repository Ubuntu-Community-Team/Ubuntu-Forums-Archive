---
title: "Can't even install Dapper"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Enigmatic on 2006-06-01
I had the same problems with Breezy, it loads the kernel and goes through loading, but then it hangs with the screen looking like this:

[IMG]http://www.gregschneider.net/IMG_3428C (Medium).jpg[/IMG]

I thought maybe it was my native res that was too high (1680x1050) so I set it to 1280x1024x32 for the install (F4 option I believe), but it didn't seem to help. I'm not sure if it actually set that res, as it just cropped out part of the screen.

---

### Post by tonyr on 2006-06-01
If you can get to the console with CTL-ALT-F1, login and
```

sudo /etc/init.d/gdm stop

```
(or kdm if your using Kubuntu).

Then edit /etc/X11/xorg.conf. Find **Section "Device"** and change the
**Driver** from whatever it is to **vesa**.  Then
```

sudo /etc/init.d/gdm start

```

That should get you a functional GUI.  After that you'll need to know what
your graphics controller is to try to fix it the right way.

---

