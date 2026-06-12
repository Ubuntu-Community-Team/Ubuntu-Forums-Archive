---
title: "So I broke GNOME"
date: 2008-11-27
forum: Desktop Environments
---

### Post by CC_Joe on 2008-11-27
And I wasn't doing anything crazy, I swear!

All I had open was firefox. I was changing the border colors on my Clearlooks theme when all of my windows greyed out. Firefox and Appearences wasn't respponding. Nothing happened when I clicked on the systray icons or the taskbar or the system menu. But the computer wasn't totally frozen: hovering the mouse over different taskbar programs showed that little popup preview feature. When I powered off and back on, GNOME doesn't start anymore. It always freezes when it says "Gnome" and those icons start to appear when it's starting up (but they don't appear anymore.)

Anyone know how to fix this? Luckily my other environments still work (In KDE now). I've been using Ubuntu for about a year and I've never broken it this thoroughly.

EDIT: And, also, does anyone know how to reinstall gnome? I think that would help my problems.


EDIT part II: Edit Harder

So, nuking all my personal settings solved the problem.

For prosperity's sake, here's what I did:

(WARNING: This will destroy all personal gnome settings, essentially giving you a default install)
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

