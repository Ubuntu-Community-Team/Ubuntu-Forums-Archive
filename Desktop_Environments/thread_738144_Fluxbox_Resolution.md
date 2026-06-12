---
title: "Fluxbox Resolution"
date: 2008-03-28
forum: Desktop Environments
---

### Post by ghandi69_ on 2008-03-28
Hey guys, I have a question about resolution settings in fluxbox.

For the last month or so I have been using a new large wide screen monitor that has a native resolution of 1900 by 1080.

With gnome, I just changed my /etc/X11/xorg file to that resolution and everyone works dandy.

However, I have been missing fluxbox and decided to go back, and while the screen still fits (both xorg and xrand say the resolution is 1900 by 1080) all the text presented in fluxbox is UNREADABLE!!

Any ideas how to fix this, or if it is even a resolution issue?

thanks,

Gandhi

---

### Post by markjensen on 2008-03-28
1900x1080 is the same whether you run KDE, GNOME, Fluxbox, e17, XFCE, ...  you get the idea. ;)

If you want to play with resolutions live in Fluxbox, you can try either X's built-in CTRL+ALT+[num pad +/-] to switch between settings.   Or, I prefer using krandrtray for playing with this.  It puts a simple graphical tool in your fluxbox panel for easy access and selection.

If you could post sample screenshots of you in Gnome and you in Fluxbox to compare, it might help.

---

### Post by RedSquirrel on 2008-03-28
> **ghandi69_ said:**
> Hey guys, I have a question about resolution settings in fluxbox.

For the last month or so I have been using a new large wide screen monitor that has a native resolution of 1900 by 1080.

With gnome, I just changed my /etc/X11/xorg file to that resolution and everyone works dandy.

However, I have been missing fluxbox and decided to go back, and while the screen still fits (both xorg and xrand say the resolution is 1900 by 1080) all the text presented in fluxbox is UNREADABLE!!

Any ideas how to fix this, or if it is even a resolution issue?

thanks,

Gandhi

Do you mean the text is too small?

I bet your DPI is too small. One easy way to fix that is to add:

```
Xft.dpi: 96
```to your ~/.Xresources file (create that file if it doesn't already exist).

---

### Post by ghandi69_ on 2008-03-29
> **RedSquirrel said:**
> Do you mean the text is too small?

I bet your DPI is too small. One easy way to fix that is to add:

```
Xft.dpi: 96
```to your ~/.Xresources file (create that file if it doesn't already exist).

That did the trick!

Thanks you guys.

---

