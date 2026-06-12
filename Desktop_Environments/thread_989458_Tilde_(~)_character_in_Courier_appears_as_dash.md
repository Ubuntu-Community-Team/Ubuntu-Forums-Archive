---
title: "Tilde (~) character in Courier appears as dash"
date: 2008-11-21
forum: Desktop Environments
---

### Post by vertigo23 on 2008-11-21
I noticed that the tilde character ("~") appears as a dash ("-") in the Courier New and Courier Pitch fonts, at least when used in gnome-terminal.  I really really like using Courier in terminal applications, and the tilde is kind of an important character in Linux and Unix, so what gives?

If this isn't fixable, can anyone recommend a good ***serif*** monospace font?  I hate sans-serif monospace.

THanks!

---

### Post by ciscosurfer on 2008-11-21
Try increasing the text/font size in the Terminal.

---

### Post by popeiler on 2013-02-09
My apologies for exhuming this thread, but it is high on search results. I have found a solution that is a bit preferable to Cisco's above suggestion of increasing font size.

I was able to resolve this issue on my system by adjusting the subpixel hinting and/or DPI setting located in: 

Settings > Setting Manager > Appearance > Fonts

set hinting=[slight]
set DPI=[102]

This will increase the effective font size slightly, but it looks much sharper than size 11 or 12 fonts do. Alternatively, changing hinting to something other than slight can resolve the issue.

---

### Post by QIII on 2013-02-09
Please do not resurrect threads that are so old.  It dilutes the effectiveness of the Forums.

Thread closed.

---

