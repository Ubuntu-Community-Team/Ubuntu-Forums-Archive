---
title: "Check box and radio button blank when selected"
date: 2008-11-25
forum: Desktop Environments
---

### Post by //yardo on 2008-11-25
Forgive me if this is in the wrong place. I don't know if this is a KDE issue or a Firefox issue...

My problem: I built a web kiosk for customers to purchase items on a company website. Pretty easy. Well, the only and final problem is that when users select an item that's a radio button or a check box the item is blank.

When I click away making the radio button or check box inactive then it shows the selected check box or radio button.

I can already hear the complaints from customers, "I selected the product but the check box doesn't show it's checked. What do I do?!?!?"

Wish I could've figured this out on my own. Please help!

---

### Post by GameManK on 2008-11-25
It's a bug in gtk-qt-engine:
[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/220575](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/220575)

Solutions:
- use konqueror
or
- go into system settings > appearance > gtk styles and fonts and disable "use my kde style in gtk applications" and choose a different style (you may need to install one to your liking)  You may need to log out and back in, or at least restart firefox, for it to take effect.  There are some threads around here about how to get firefox to look nice in KDE without using gtk-qt-engine.

---

