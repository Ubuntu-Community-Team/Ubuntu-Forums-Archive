---
title: "changing into safe/low graphics mode"
date: 2008-12-31
forum: General Help
---

### Post by arohanui on 2008-12-31
This is related to problems I'm having not being able to find a driver for my monitor: [Viewsonic VA2226w under 8.4]("http://ubuntuforums.org/showthread.php?t=1026645").

Sadly, I was experimenting with the default display resolutions, trying to find one that would give me the correct aspect ratio at least, and now all I can see is garbage.  How do I get back into safe graphics mode so I can change it back to something that I can at least see?

I did r'd.t.f.m. but I can't find the answer.
It did occur to me that I was being dense, and that I could do it from GRUB, but it's ignoring my frantic mashing of escape for some strange reason.  And ctrl-alt-# from within Ubuntu isn't working either.

Can anyone help me out here?

---

### Post by arohanui on 2008-12-31
Oh please help me, google isn't helping either.

If I can't get to the GRUB menu, and I can't switch to a tty, what am I going to do?  Reinstall the 7.10 OS from CD?  Cause that's what I'm looking at if no one can help me out.  Either that or using the system as an expensive door stop.

---

### Post by Dr Small on 2008-12-31
How about trying to edit /etc/X11/xorg.conf from the console.
Find:
```
Section "Device"
```

And in the Driver option, change it to say "vesa", like this:
```
	Driver      "vesa"
```

See if that helps any. Save the file, go back to your X11 Session and restart it with CTRL + SHIFT + BACKSPACE

---

### Post by arohanui on 2009-01-01
Okay, well ctrl-alt-# didn't work, but ctrl-alt-F# did.  So at least I was able to get in and to /etc/X11/xorg.conf.  Now I just need to find a configuration that actually works.

---

### Post by arohanui on 2009-01-01
Oh thanks for replying Dr Small.  

Unfortunately it _was_ set to vesa.  I changed it to nv, and that didn't work either.

---

### Post by arohanui on 2009-01-01
I think I need to look up the horizsync/vertrefresh info for the VA2226w, and enter in manually.  I'll give it a whirl.

---

### Post by arohanui on 2009-01-01
Never mind, following advice I found out there in the aether, I ran 

sudo dpkg-reconfigure xserver-xorg

and when I restarted X11, it dropped me into something workable, even if it is at 1024x768, rather than 1600x1050.

---

