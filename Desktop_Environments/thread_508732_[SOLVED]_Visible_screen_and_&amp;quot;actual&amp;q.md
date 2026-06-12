---
title: "[SOLVED] Visible screen and &amp;quot;actual&amp;quot; screen don't match!"
date: 2007-07-24
forum: Desktop Environments
---

### Post by jdackle on 2007-07-24
I originally asked about this in [another thread]("http://ubuntuforums.org/showthread.php?p=3073849#post3073849") as it might be the same problem as originally described there. As I understood it wasn't, I'm posting a new thread here. My apologies to the moderators if this is considered cross-posting or something - not my intention...

So... here's the thing:
- My video card is: ATI 3D Rage Pro (AGP)
- Maximum resolution is 1152x864 but I prefer 1024x768
- In order to get that 1024x756 resolution, In /etc/X11/xorg.conf I changed:
```
"1152x864" "1024x768" "800x600" "720x400" "640x480"
```
to
```
"1024x768" "1152x864" "800x600" "720x400" "640x480"
```
everywhere that line appeared.
- In result, I now do have a 1024x768 display only not quite... The visible area is 1024x768 but the screen is not "complete" - if I move the mouse pointer upwards (or downwards, left or right) beyond the visible area limits, it will "move up" and show the top (bottom, far-left, far-right) of the screen! This means if I have a panel at the bottom I'll have to move the mouse pointer down to "move" the visible area down and actually see it ( and thus hiding more of the topper part of the screen.
- This affects both th GDM login-screen as well as the window manager display (currently Openbox).
- I could workaround this when using GNOME by leaving xorg.conf in its original setup and defining the Gnome Desktop's resolution to 1024x768. But now I'm using Openbox and I don't know how to set that up there. And anyways... Even if I could... It's still strange. But I'll take that on if nothing else! ;)

Apreciate any help! :)

Cheers!

---

### Post by jdackle on 2007-07-24
I found a workaround for this! :)

In the command-line:
```
xrandr 1024x768
``` will do the trick.

Now I jsut have to get acquainted with the *autostart* configuration of Openbox and I'm almost all-set!

To be completely set, I'd need to do that to GDM to.
So til I can implement this in both "spaces", I'll leave this as UNSOLVED.

Your help is still welcome! ;)

Cheers!

---

### Post by RedSquirrel on 2007-07-24
The easiest way to fix this is to remove the entry for "1152x864". If 1024x768 is the largest entry in that list, that will do what you want:

```
"1024x768" "800x600" "720x400" "640x480"
```

If you leave it in, then the "virtual" desktop size is 1152x864 which is why you can scroll around it with your mouse (you're only seeing a 1024x768 window of the 1152x864 desktop).

You can also add a line like this just below your list of resolutions:

```
Virtual 1024 768
```

to force the desktop to be 1024x768, but just removing it from the list is easier...

---

### Post by jdackle on 2007-07-24
Thanks! Awesome! :D

---

### Post by RedSquirrel on 2007-07-25
You're welcome. The funny thing for me is that whenever I see this question I always think back to my first installation of windows 3.1. The graphics card I had at the time had this sort of functionality. You could have a virtual desktop that was larger than your monitor's resolution and you could scroll around the desktop with the mouse. It sounded like a neat idea, but I found that in practice it was just annoying. ;)

---

### Post by jdackle on 2007-07-25
:lolflag:

Yes it does sound like a neat idea and it is anoying!

Thanks again. Worked fine. :)

---

