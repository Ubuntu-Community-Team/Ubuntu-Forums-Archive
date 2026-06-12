---
title: "KDE 4 Plasmoids Lost / Desktop panels broken / Horror story"
date: 2008-12-30
forum: Desktop Environments
---

### Post by Newbie123 on 2008-12-30
Hi,

I've recently been having a lot of problems with KDE 4.1. I am running Kubuntu 8.10.

First, I attempted to add a widget to my panel - this was a big mistake. Everything on the panel got screwed up. The clock suddenly took up half of the panel, and I couldn't resize it, only move it around. I rebooted the system, but this didn't do anything.

I then tried playing around with the 'add widget' menu. The GUI was a little confusing, so I accidentally removed my KNotes widget. I added it back again, but now all my notes are gone!

With my panel completely broken, I decided to remove it. This was a bigger mistake. I added the panel back, but now all of my apps in the system tray are missing, namely:

-Current input language icon. I can switch languages with CTRL+ALT+K, but there is no icon
-Kmixer sound icon
-The KDE clipboard icon
-Laptop battery life icon (I think you can set your notebook's performance with this too)


1. Is there any way to get my notes back?
2. Is there any way to reset the panel back to the default?

If anyone can help me with 1 and 2, it will be greatly appreciated.

---

### Post by benerivo on 2008-12-30
I think when you remove widgets, they lose their settings / saved state, so your notes might be lost. The icons in the system tray should reappear when you add the system tray plasmoid back to the panel (i think the battery icon may be a separate plasmoid, and so needs to be added separately). You can get back to defaults by deleting a file and then using Ctrl+Alt+Backspace. I think what you need to delete is```
~/.kde/share/config/plasma-appletsrc
```

EDIT - Also, have you checked the options in System Settings for the keyboard layout, as from memory, i think there is an option for having an icon displayed for quick changing.

---

### Post by Newbie123 on 2008-12-30
Thanks, deleting the file worked wonders. Everything seems to work now.

It is unfortunate that my notes are lost. I will try to find another desktop note app for the future.

Thanks again. This was most helpful.

---

### Post by Doncr on 2008-12-31
Pretty bad about your notes. Not good default behaviour. Tomboy is a good alternative though :-).

---

### Post by clb62 on 2009-08-22
Another newbie, but did not have as much tied up in notes as Newbie123, but I was able to recover using benerivo's suggestion after some "perilous panel edits" of my own.

2 solutions in 1 night (including my wireless).  I hope my luck continues with these forums!

:)

---

