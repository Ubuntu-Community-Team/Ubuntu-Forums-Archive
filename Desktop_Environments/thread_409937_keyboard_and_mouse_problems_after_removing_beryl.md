---
title: "keyboard and mouse problems after removing beryl"
date: 2007-04-15
forum: Desktop Environments
---

### Post by sblanzio on 2007-04-15
hi!
Due to several Beryl problems, i decided to remove that.

I uninstalled all beryl, emerald packages and hoped everything would have come back to normality. but this didn't happen.

After reboot i continue having very annoying problems like: my "Alt" key doesn't work.
When I press Alt, the first time, suddenly my "NumLock" led shuts off, and I can't even switch between windows with Alt+Tab. Either, I can't use any other shortcut like Alt+F2...
Pressing Alt is like pressing nothing.

I found out i can fix it temporarly making some change in System->Preferences->Keyboard window. I just have to change some value and then changing again just like it was, and most of the times, after clicking the "num lock" key, I can use the "Alt" key. But after reboot the problem comes back.

I even have mouse troubles.
I can focus windows only by clicking on the title bar. If I try to click on a unselected window body, it just select what I clicked, but it doesn't really focuses the window!

I noticed that when i can fix the Alt key, this mouse problem solves. but again, as I reboot these problems are still there.

Is there a way to recover the normal Alt key and focusing management?

I tried everything in System menu but nothing seem to be a definitive solution.

thank you!
sblanz

---

### Post by Seisen on 2007-04-16
Type this in the terminal and follow the steps and see if it helps.

```
sudo dpkg-reconfigure xserver-xorg
```

---

