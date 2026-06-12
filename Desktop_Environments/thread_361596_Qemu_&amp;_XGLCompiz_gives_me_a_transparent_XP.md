---
title: "Qemu &amp; XGL/Compiz gives me a transparent XP"
date: 2007-02-14
forum: Desktop Environments
---

### Post by Foechoer on 2007-02-14
Hello,
I just installed Qemu to emulate a WindowsXP on Dapper..
Everyting works perfect except one thing...
When I run it in XGL with compiz,  it is like tranparent...  I dont have this problem on Gnome..
I did my research and found this:
```
XLIB_SKIP_ARGB_VISUALS=1
``` 

But it doesnt seems to do anything..
I tested it in my starter like this:

```
XLIB_SKIP_ARGB_VISUALS=1 qemu -boot c -hda winxp.img -m 512 -localtime
```
I also tried to do it,  and after run the qemu thing..  but still nothing.

What can I do?


btw,  I used this tutorial: [http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html)

---

### Post by mssever on 2007-02-14
Try rolling your mouse wheel up while holding Alt. I use Beryl instead of Compiz, but in the Beryl settings app, there's a place to set window attributes by various criteria. If Compiz has something similar, you can permanantly turn off transparency for that window.

---

### Post by Foechoer on 2007-02-15
I already tried changing transparency manual,  with the Alt MouseWheel but that didn't do it.
Compiz also has a manager..
do you know under which menu I can find it?  Where is it in the beryl-manager?

---

### Post by mssever on 2007-02-15
Well, beryl-manager looks quite a bit different from the screenshot you posted, but it's located under Window Management > Set Window Attribs by various criteria > Window Opacity.

Here's a screenshot of Beryl-manager for comparison. In my setup, some windows (dialogs, tooltips, menus, etc.) are transparent, while others (normal windows, fullscreen windows, etc.) are not. Maybe Qemu is using a strange window type.

Also, you might disable transparency completely and verify that Qemu/XP is normal. Otherwise, something is very strange indeed...

---

