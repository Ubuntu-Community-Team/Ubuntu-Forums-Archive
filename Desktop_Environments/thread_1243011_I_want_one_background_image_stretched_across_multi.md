---
title: "I want one background image stretched across multiple desktop cube desktops. Compiz?"
date: 2009-08-17
forum: Desktop Environments
---

### Post by DestroyerOfTheSeas on 2009-08-17
"Across Multiple Desktop Cube Desktops," try saying that five times fast.

I've got the spherical DesktopCube distortion enabled via CompizConfig. Its three desktops wide. Has anybody figured out a way to stretch one background image across all three desktops? Has anybody else tried doing this?


Thanks alot for viewing, chaps!

Edit:
Any ideas at all? I'm still having no luck.... :(

---

### Post by DestroyerOfTheSeas on 2009-08-20
Alright, this is what I've begun to try. I have three desktops on my cube, and what I'm trying to do is chopone image in three sections and have compiz draw my background images seperately on each desktop. The problem I've run into now is disabling nautilus from drawing the desktop so compiz can do it.

I went into the gconf editor, and navigated through apps > nautilus. I was looking for some sort of option to disable the drawing of the desktop, however it was absent.

In the terminal I tried this:

> gconftool -t bool /apps/nautilus/preferences/show_desktop -s false

The only result I had from that was my desktop cube spherical deformation was no longer working, so I set it back to true.
I'm not too sure what to try next, any ideas, anyone?

---

### Post by mgmiller on 2009-08-23
What you are trying to do is get a different wallpaper on each face of the cube (or sphere in your case)  This has been sought after for a while with different degrees of success.

Try looking here:
[http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html](http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html)

---

### Post by MichaelRX8 on 2009-08-23
Pretty sure it can be done....check out my avatar ;-)

---

### Post by DestroyerOfTheSeas on 2009-08-30
You are absolutely right, mgmiller. However I've run into trouble disabling nautilus from drawing the desktop. I used gconf-editor and navigated to nautilus' prefrences and unchecked the box next to "show desktop," which as predicted took away my desktop icons, but unpredictably disabled my sphere distortion and did not take my desktop background away.

---

