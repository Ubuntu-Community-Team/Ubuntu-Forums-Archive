---
title: "Openbox + xcompmgr + tint2 redraw problem?"
date: 2010-09-24
forum: Desktop Environments
---

### Post by jensvdb on 2010-09-24
Hello everyone!

It's been almost one week since I've installed Openbox, xcompmgr and tint2.
So far, so good...:)

There is only one problem... When I minimize an application, chances are that part of the window's title bar is not erased (ref. to the attachment for an example). This does not always happen, though...

The same thing happens when I let tint2 autohide itself (so when I minimize an application while the taskbar is not visible).

The "piece-of-titlebar" disappears, however, when I ask the window manager to repaint that region (for example: right click so the Openbox-menu draws "over" the leftovers of the minimized window).

Does anyone have the same problem (or better: can someone help me with this somewhat annoying problem:P)?

Thanks,
jensvdb

---

### Post by leef on 2010-09-24
Hi,

I think that it might be either xcompmgr or your graphics card but based on the fact you're using openbox, my guess is that it's xcompmgr that's the problem. I don't think we need fancy effects my openbox using brother.

---

### Post by thil77 on 2010-09-25
if the problem is visible only in tint2, it could be tint2.
otherwise, it's xcompmgr problem.

you can try another composite manager (like cairo-compmgr).

---

### Post by jensvdb on 2010-09-25
> **leef said:**
> Hi,

I think that it might be either xcompmgr or your graphics card but based on the fact you're using openbox, my guess is that it's xcompmgr that's the problem. I don't think we need fancy effects my openbox using brother.

True.:)

Thank you for the reply.

---

### Post by jensvdb on 2010-09-25
> **thil77 said:**
> if the problem is visible only in tint2, it could be tint2.
otherwise, it's xcompmgr problem.

you can try another composite manager (like cairo-compmgr).

I've just tried your solution, and have had some issues with Conky (i.e. it stays on top of all other windows). For now, I think I'll just disable those fancy minimizing effects, like *leef* suggested.

If tint2 would be the problem, I think it's weird that there aren't any threads on this forum describing my problem... It could indeed be a hardware related problem, though.

Anyways, thank you for your suggestion:)

---

### Post by ibuclaw on 2010-09-25
> **jensvdb said:**
> I've just tried your solution, and have had some issues with Conky (i.e. it stays on top of all other windows). For now, I think I'll just disable those fancy minimizing effects, like *leef* suggested.


tbh, when I use xcompmgr, I never use any fancy rendering effects. Just a basic xcompmgr -s, or -n. So long as true transparency is working, can't really complain about anything else. :)

---

