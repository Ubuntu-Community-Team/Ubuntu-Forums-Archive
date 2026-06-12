---
title: "Desktop launcher"
date: 2006-02-02
forum: Desktop Environments
---

### Post by art on 2006-02-02
Ok, the most weirdest thing I have ever seen. So I installed iTunes with crossover (please don't tell me what gnome alternatives I have, I know them, i want to use iTunes). It created desktop shortcut and entry in menus. So when I launch menu entry i don't have sound. When I launch the desktop shortcut i DO have sound! If I then create a panel entry for iTunes pointing to the same file shortcut points to, i do NOT have sound:confused: Can anyone explain what's going on, I am completely clueless...
Thanks

---

### Post by art on 2006-02-03
bump

---

### Post by art on 2006-02-06
Just for people who like me encounter this problem, it got solved after running CrossOver configuration editor and changing the sound driver to alsa (default oss). I still don't know why it would run when launched from desktop but now from menu...

---

### Post by fakeollie on 2006-02-19
I may be dead wrong here, but I don't think CrossOver configurations have anything to do with it. Weirdly enough, this same thing happens to me in a rather different scenario. Allow me to elaborate, please.

I recently installed and configured bluetooth support to send/receive files to and from my phone. I use Ubuntu Breezy. Anyway, I created a desktop launcher for gnome-obex-send. When I drag files over it, they get sent to the phone. It works every single time.

But if I make the exact same launcher in a panel -- I'd love to have a little bluetooth icon in the bottom panel next to the workspace changer, opposite the trash -- it doesn't work. When I drag a file there, gnome-obex-send opens, I select the phone, but then it doesn't connect. It's as if when lauched by the panel, the app runs with different permissions from the current user, which, to me makes no sense at all.

Regardless of that being the case, from what I've seen and reading your posts above, I think it's safe to say panel launchers behave in a different way from their desktop counterparts. I'd love if some of the experienced ubuntu gurus could shed a light on this issue, maybe provide a solution or identify what we're doing wrong.

Cheers.

---

### Post by GameGod on 2006-02-19
This happens because ESD is using your soundcard when you launch from the menu/panel, but isn't when you launch from your desktop.
(ie. You hear the ubuntu click sound on the former two cases...)

I'm not sure what the best solution is... probably to switch Crossover to ALSA or something or to just launch stuff from the desktop...

---

