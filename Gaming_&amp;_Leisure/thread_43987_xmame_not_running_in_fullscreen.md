---
title: "xmame not running in fullscreen?"
date: 2005-06-24
forum: Gaming &amp; Leisure
---

### Post by bigcletus on 2005-06-24
I have tried several different versions of xmame.  The first one I used apt-get and recieved the old 0.86 version.  Since then, I downloaded 0.96 and it works great but has the same problem I had with the other versions I tried:  I cant get full screen in normal video mode.  Xvid mode and GL mode both do full screen (they also look identical) but I can't get normal video mode to display in fullscreen.  Just in the little tiny window. Am I missing something?  Thanks for any help.

---

### Post by elvis on 2005-06-24
No, that's normal.  Only Xv and OpenGL can stretch to fullscreen.  The normal mode is Windowed only, and non-stretchable.  You can define scale modes at execute time however, but the scaling is done by XMAME, and not the graphics blitters.

Both also give you options for bilinear filtering, which can be turned off if you don't like the "blurry" look.

If you haven't already created an xmame config file to hold values without having to enter them via the command line every time, you can do this:

```

xmame --showconfig > ~/.xmame/xmamerc

```

And then edit your ~/.xmame/xmamerc file to hold values permanently.

---

### Post by bigcletus on 2005-06-24
[QUOTE=elvis]No, that's normal.  Only Xv and OpenGL can stretch to fullscreen.  The normal mode is Windowed only, and non-stretchable.  You can define scale modes at execute time however, but the scaling is done by XMAME, and not the graphics blitters.

Both also give you options for bilinear filtering, which can be turned off if you don't like the "blurry" look.

If you haven't already created an xmame config file to hold values without having to enter them via the command line every time, you can do this:

```

xmame --showconfig > ~/.xmame/xmamerc

```

And then edit your ~/.xmame/xmamerc file to hold values permanently.[/QUOTE]
 and all along I thought I had messed it up somehow :)  Thanks for the great info :)

---

### Post by andlinux21 on 2006-02-03
Can you recommend some values for a nice sized window?

---

