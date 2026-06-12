---
title: "xfce panel content left-aligned after upgrade"
date: 2009-10-09
forum: Desktop Environments
---

### Post by Redsandro on 2009-10-09
Hi,

After I upgraded Xubuntu 8.10 to 9.04, everything in the bottom panel was left-aligned. But originally, desktop miniatures and some icons like trash can are supposed to be right aligned.

I think I also had this after upgrading from 8.04 to 8.10, but then I just redid a clean install. But I don't want to do that now over something simple.

It's probably something extremely simple. But I cannot move it to the right of the screen, only farther to the left or to the rightmost part of the other left-aligned stuff. I also don't see align options in properties.

How do I fix my panel?

---

### Post by sisco311 on 2009-10-09
Right click on the panel -> Add New Items -> Separator or Spacing -> Expanding empty space.

Move the items to the right of the separator.

If you want to restore the default panels, rename (or delete) the *~/.config/xfce4/panel/* directory and restart xfce4-panel.

```
mv  ~/.config/xfce4/panel ~/.config/xfce4/panel-backup
```
```
killall xfce4-panel
```

If the panel doesn't restart automatically, then
press Alt+F2 and run:```
xfce4-panel
```

---

### Post by Redsandro on 2009-10-09
Nice, thank you!

---

### Post by krainey2106 on 2009-12-01
Thanks Sisco311,

I had a similar problem in xubuntu 9.10--no panels top and bottom for me, the system administrator.  Other users had panels.  I ran ¨xfce4-panel¨ , without a preceding ¨killall¨ command, and this solved the problem.

---

### Post by perdubug on 2012-12-20
I had similar problem on Xubuntu 12.04 with xfce4 4.8.6 - panel2 is left-aligned instead of center aligned. The solution is simple - Open 'Panel Preferences'->'Diaply' tab->Uncheck 'Lock panel',then drag your panel2 to a right position. Remember to lock it again if you like.

---

### Post by Toz on 2012-12-20
Thank you for sharing, but this thread is 3 years old. Closing.

---

