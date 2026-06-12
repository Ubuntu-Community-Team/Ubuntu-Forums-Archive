---
title: "GUI/Display Problem"
date: 2009-01-18
forum: General Help
---

### Post by Dave009 on 2009-01-18
When I log into Ubuntu 8.10, I get asked at the command line to select a display (ie 1440x900x32 or 1440x900x8, VGA and VESA modes). I select my native resolution, 1440x900x32. The startup process continues, except now I have to login through the command line, and bash reports a stream of 'access denied' messages. Now, I have no GUI and am forced to operate solely from the command line.

The background to my problem is that I was trying to make my GRUB and usplash look nice. The first thing I did was install Splashy, and add 'vga=791' to the Ubuntu option in my menu.lst. Then, I added Start-up Manager to make modifications easier (at this point, everything worked). Then, and this is where the problems began, I changed the line in my menu.lst to 'vga=80' (stupid move I know, because I'm not sure what it means - I just wanted the 800x600 resolution on boot), and installed [this usplash screen]("http://gnome-look.org/content/show.php/Ubuntu+Usplash+Smooth?content=93386") independently of Start-up Manager. My GUI is now broken, and I'm not sure how to edit menu.lst in the command line, because even when I'm logged in as root, vim won't let me edit it (read-only). 

I need to fix this ASAP because I need to use Linux for school, so any help or insight is greatly, greatly appreciated.

---

### Post by DylanW on 2009-01-18
start with this

```
startx
```

---

### Post by Dave009 on 2009-01-19
> **DylanW said:**
> start with this

```
startx
```

That didn't work for me, temp files couldn't be created or something of that nature. I'm also in the same predicament when I remove the 'vga=791|800' (I tried both). And when I boot, bash echoes "\dev\null\: Permission denied" a bunch of times.

---

### Post by Dave009 on 2009-01-20
Ok, I solved the problem of not being able to launch startx - my disk was read-only. So I ran the command 'mount -o remount,rw/' and that seemed to work - I could edit my menu.lst now, and launch startx. However, when I did, I get the message 'User Switcher has quit unexpectedly', then my keyboard/mouse do not work, and I can only restart/shutdown the system, or exit the GUI. Any ideas?

I'm going to try and uninstall the usplash .deb package, and see if any progress is made.

---

