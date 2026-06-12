---
title: "When I set CompizConfig to cycle wallpapers nothing happens."
date: 2011-06-30
forum: Desktop Environments
---

### Post by Nitrozzy7 on 2011-06-30
I've set all the wallpapers I want to cycle, I've set the time to 15 sec checked the "Cycle" box but nothing happens. The background stays the same. Log in-out didn't work.
I'm on Ubuntu Classic

---

### Post by nzjethro on 2011-06-30
Have you stopped Nautilus from drawing the background?

Try
```
sudo gconf-editor /apps/nautilus/preferences/show-desktop
```

then deselect the "Show Desktop" box. There's a full command for it, but I can't remember it.

**EDIT:** found the command. It is:

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```

---

### Post by Nitrozzy7 on 2011-06-30
worked but I can't see the desktop icons. I think I'll work around it but I want to know if I can make them appear again.

---

### Post by nzjethro on 2011-07-01
Ah yes, perhaps I should have mentioned that that would be a side effect. :)

Nautilus won't draw icons onto what it believes is a "non-existent" desktop, so you can't have both Compiz wallpapers and desktop icons at the same time.

I got around it by having a dock (I used Talika, but there are plenty of others out there). You can still access the files and folders (and even shortcuts) on your desktop if you navigate to the desktop either in your file manager or on a terminal:

> cd ~/Desktop

---

### Post by Nitrozzy7 on 2011-07-01
Isn't there a way to have both? I'm not necessarily mean to combine them. What I'm saying is if there's a way to customise the cycle and the wallpapers that appear under "change desktop background". I've seen some pre installed space-themed wallpaper cycles.
By the way; How to enable .gif animations as background?

---

### Post by Nitrozzy7 on 2011-07-01
Nevermind! I downloaded "DesktopNova" and I switched back the values to

```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true
```

Works just I wanted to.
Thunx!

---

### Post by nzjethro on 2011-07-02
Cool, DesktopNova looks interesting, I may have to have a play around with it. Glad you got it behaving how you wanted.

---

