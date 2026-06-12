---
title: "All icons missing in Kubuntu Desktop"
date: 2008-09-19
forum: Desktop Environments
---

### Post by MatthewHSE on 2008-09-19
I installed Ubuntu a couple days ago, but I found I prefer the KDE desktop so I installed the Kubuntu desktop:

sudo aptitude install kubuntu-desktop

However, when I login to KDE, ALL the icons are gone from the panels, menus, desktop, etc.

I'm guessing there's a simple solution to this, but I don't know what it is.  Do I just download an icon pack or something, or is there something else I need to install?

---

### Post by kjohansen on 2008-09-19
the problem is that KDE and GNOME have their own file managers, and these file managers manage the desktop too.  To restore the desktop you will have to either allow nautilus to control the desktop or recreate your desktop in KDE (I think KDE's manager is called dolphin)

To allow nautilus to control the desktop type 
```

nautilus &

```
in a terminal.  You will also need to add this to the start apps to make it permanent.  this wont do anything about the panels though.

---

### Post by MatthewHSE on 2008-09-20
Thanks for the info. I'm not sure I understand how to recreate my desktop in KDE, but at least that's something to research.

In the meantime, is there *anything* to restore icons to the panels in KDE, particularly the notification area?

---

### Post by kjohansen on 2008-09-21
when I said recreate, I just mean make the icons again (right click, create launcher, add the command for the application).

i do not beleive there is any way to transfer the GNOME panel icons to KDE.  But KDE should have very similar panel icons if you right click on the panel and select "add"

---

