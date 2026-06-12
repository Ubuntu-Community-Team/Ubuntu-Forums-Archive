---
title: "Beryl Manager Freezing Computer"
date: 2007-01-04
forum: Desktop Environments
---

### Post by rickatnight11 on 2007-01-04
I'm running a Dell Inspiron 6000 with an Intel 915GM Graphics Controller.  I have followed multiple guides for intel configuration of Beryl and I still can't get it to work.  I have gotten the program running with ```
beryl-manager
``` and the emerald icon did appear, but when I changed the window manager setting from Metacity to Beryl the windows lost their titles and the computer froze.  Now whenever I run the "beryl-manager" command it immediately freezes the computer with the following code in the Terminal:
```
$beryl-manager
$XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
```

That's as far as it gets and there is no keyboard or mouse response.  I have seen threads with similar code output like mine but nothing definitive.  Can anyone be of assistance?  I have a picture of my screen with this text that shows how the title bars disappears if anyone is interested.

---

### Post by 23meg on 2007-01-04
Try this ```
beryl --use-cow --force-aiglx
```

---

### Post by rickatnight11 on 2007-01-04
Well the mouse still moves but when I type that command the desktop and menus disapear as well as the title bar to the Terminal.  System freezes like normal.

---

### Post by rickatnight11 on 2007-01-05
Any other ideas?  I'd love to get it working.  What dependencies are required for Beryl?  Maybe I don't have one.  Also how do I ensure that I am using the appropriate driver for the graphics controller.  I believe it's the i810 driver as from what I have read this performs the best.

---

### Post by rickatnight11 on 2007-01-05
Well I tried using someone's xorg.config file but I received the same problem.  I don't believe that the issue is with Beryl but either the Intel driver or a dependency.  Anyway, here are some pictures of the problem and maybe someone can help me out.

[[IMG]http://img353.imageshack.us/img353/1456/p1010165fw6.th.jpg[/IMG]](http://img353.imageshack.us/my.php?image=p1010165fw6.jpg)
[[IMG]http://img169.imageshack.us/img169/9704/p1010166bb7.th.jpg[/IMG]](http://img169.imageshack.us/my.php?image=p1010166bb7.jpg)
[[IMG]http://img169.imageshack.us/img169/5669/p1010167vq5.th.jpg[/IMG]](http://img169.imageshack.us/my.php?image=p1010167vq5.jpg)

---

