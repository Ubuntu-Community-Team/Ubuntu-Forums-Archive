---
title: "The taskbar in Xfce?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by erik-the-red on 2006-02-11
My taskbar suddenly disappeared.

The panel with the Xfce "start menu" is still there at the bottom, but the location for all my minimized apps (ie. the taskbar) at the top isn't there anymore.

How can I get it back?

---

### Post by cutOff on 2006-02-11
Have a look [here]("http://doc.gwos.org/index.php/DesktopUIBreezy").

---

### Post by taurus on 2006-02-11
Any change you have nautilus running in Xfce4???

---

### Post by erik-the-red on 2006-02-11
cutOff, I didn't find anything there that helped me out :(

taurus, I don't think so because GNOME is still fine.

---

### Post by aysiu on 2006-02-11
Have you tried Alt-F2 and ```
xftaskbar4
```

I'm not 100% sure that's the command, as I no longer have XFCE installed, but if you open a terminal and type ```
xf
``` and then hit the **Tab** button twice, it'll tell you what the exact command is.

---

### Post by taurus on 2006-02-11
Let's try it this way.  Some people like to use Xfce4 but love to make it behave like Gnome so instead of using the taskbar that comes with xfce4, they have nautilus running.  It has nothing to do with whether Gnome is running fine or not...  If you are not sure, type this at the prompt and look thru it to see which one you have it running, nautilus or xftaskbar4.

ps -A

---

