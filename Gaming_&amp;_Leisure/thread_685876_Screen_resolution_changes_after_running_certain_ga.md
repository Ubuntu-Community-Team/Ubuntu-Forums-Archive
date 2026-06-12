---
title: "Screen resolution changes after running certain games"
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by Dritzen on 2008-02-02
I run Gnome at 1280 x 800 resolution.  When I run Quake 3, it is at 1024x768 resolution.

After I exit Quake3, the screen will be 1280x800 but zoomed in.  The only way I can set the resolution back to normal is to change to a different resolution and then switching back to 1280x800.

Is there a command that can do this for me?  Any suggestions on how to keep this from happening?

---

### Post by DoktorSeven on 2008-02-02
I have a shortcut that fixes things when this happens -- though that shouldn't happen often, like generally after a game crashes or something.

```
xrandr -s 1 && xrandr -s 0
```

Open a terminal, type **xrandr** and you'll see a list of the modes available, the 0 and 1 are which line in this list, starting with the top as 0, is set when you use -s.

I do it twice because sometimes it gets "stuck" on its chosen resolution and I have to change to another one before going back to my default.

---

### Post by Dritzen on 2008-02-02
That did the trick.  Thank you

---

