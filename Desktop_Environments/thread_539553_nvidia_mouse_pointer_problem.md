---
title: "nvidia mouse pointer problem"
date: 2007-08-31
forum: Desktop Environments
---

### Post by dubrict on 2007-08-31
I've been having a recurring problem with my mouse pointer.  I have a 6600gt, and my mouse pointer likes to become invisible whenever it's supposed to be the hourglass-icon. (the rotating wheel in ubuntu.)  I've had this problem before in other distros, and with both KDE and Gnome.

I read in one post to disable HWCursor in the xorg.conf file, but that's not a sufficient solution.  It does work, but it also causes there to be quite a bit of artifacting on the screen, mainly because what's under the pointer doesn't seem to be redrawn correctly when the pointer is moved.  I imagine this probably has to do with the software cursor's interaction with compiz.

Does anybody else know what I'm talking about, or have a solution?  Note that the pointer goes invisible ONLY when it's the hourglass....

---

### Post by Trevor Bramble on 2007-08-31
So you're saying it goes invisible only for the duration of the intended hourglass animation, and then is visible again, or that it becomes invisible from that point on?

I hadn't connected it to the hourglass, but my pointer has been going invisible often as well.  Often when switching windows.  It happens more often than not with the Gnome Terminal and Pidgin, though that's probably just because of frequency of use.

I wondered if it might be a Gnome thing, so I actually swapped it for Xfce again ...and then swapped back when it happened there too.

I'm on 7.04, also Nvidia (6600LE x2), and it's driving me nuts too.

---

### Post by dubrict on 2007-08-31
Yeah, it only stays invisible for the duration of the hourglass.
It's as if the files that have the pointer images are corrupted, but that wouldn't explain why it's happened to me several times, on multiple distros.

---

### Post by Trevor Bramble on 2007-09-19
[This]("http://ubuntuforums.org/showthread.php?t=524466") solved it for me, but now of course I can't use "Desktop Effects".  Real bummer.

---

### Post by Sutur on 2008-01-12
Force hardware cursor.

Add this:

```
Option "HWCursor" "True"
Option "SWCursor" "off"
```

To the devices section of your xorg.conf file in /etc/X11.

This works for me, and I had *exactly* the same problem as you with compiz enabled.

---

### Post by Sutur on 2008-01-18
Just realized that this issue only appears in gnome, and not in xfce4.

Anyone throw some light onto this matter?

---

### Post by Trevor Bramble on 2008-01-21
I had switched to XFCE as well to see if Gnome had anything to do with it.

Nothing changed.  Same for KDE.

I'm on a System76 Serval v3 now, and the problem hasn't come up at all (not that I expected it).  The tower is going to be a dedicated gaming (read: Windows) PC now, with the occasional just-for-kicks GNU/Linux distro finding its way into it sometimes.

Best of luck to the rest who still suffer from this.

---

