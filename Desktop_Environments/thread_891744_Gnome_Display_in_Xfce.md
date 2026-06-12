---
title: "Gnome Display in Xfce?"
date: 2008-08-16
forum: Desktop Environments
---

### Post by stargirl51 on 2008-08-16
For some reason, after I hit "Alt+F2" and typed in gksudo nautilus in xfce, the display interface is suddenly gnome. As in Xfce is not my default display settings manager when I'm in Xfce. So how do I under whatever I did with "gksudo nautilus"? 

Would it be to go back into the terminal and gksudo whatever the xfce display manager is?

Some notes:
- No, I did not type or change anything after typing in gksudo nautilus. I just closed the window.
- When I start up Xfce, it has the xfce interface but when it fully loads, it looks like gnome.
- Yes, I have tried removing xfce and reinstalling xfce

Any and all help is appreciated.

---

### Post by kidux on 2008-08-16
Nautilus is Gnome's desktop manager as well as it's file browser, so when you typed in gsudo nautilus it launched it as such. If you just want to browse files with it type ```
gksudo nautilus --no-desktop
```

That should take care of the problem, but why would you use nautilus instead of Thunar?

---

### Post by Cheesehead on 2008-08-16
Gnome --> Nautilus
XFCE  --> Thunar

Though the two are (relatively) compatible. So you can run Nautilus from XFCE, and you can run Thunar from Gnome. But, yeah, it may look unusual.

As long as your machine is fast enough and has capacity enough to handle both, use whatever you prefer.

---

### Post by stargirl51 on 2008-08-16
> **kidux said:**
> Nautilus is Gnome's desktop manager as well as it's file browser, so when you typed in gsudo nautilus it launched it as such. If you just want to browse files with it type ```
gksudo nautilus --no-desktop
```

That should take care of the problem, but why would you use nautilus instead of Thunar?

thanks, Kidux. Well I wanted to attempt to create my own gdm theme. But I panicked when I typed in "gksudo nautilus" because something flashed and system beeped. So I closed it and have been confused since, haha.

---

### Post by kidux on 2008-08-18
> **stargirl51 said:**
> thanks, Kidux. Well I wanted to attempt to create my own gdm theme. But I panicked when I typed in "gksudo nautilus" because something flashed and system beeped. So I closed it and have been confused since, haha.

Oh, that's funny! :lol: You'll have to link to the theme when you're done. Is it dark or light?

---

### Post by stargirl51 on 2008-08-20
That's the thing. I barely nicked into it when things went haywire. I'm still learning how to from watching forums and gnome-look.org

---

### Post by stargirl51 on 2008-09-03
> **kidux said:**
> Nautilus is Gnome's desktop manager as well as it's file browser, so when you typed in gsudo nautilus it launched it as such. If you just want to browse files with it type ```
gksudo nautilus --no-desktop
```

That should take care of the problem, but why would you use nautilus instead of Thunar?

I've tried it and it returns the desktop theme to Thunar but whenever I start xfce, the hardy heron desktop still shows up? Well the hardy heron wallpaper/icon set.

I would like the themes to be separate so I would be able to differentiate between the two DEs.

Is there no way for it to go to Thunar and have it stay that way?

Cheers,
stargirl

---

### Post by bobby555 on 2008-10-15
I believe you can go to System->Preferences->Sessions (may be named slightly differently) and click save current session on the rightmost tab. Does it work?

A

---

