---
title: "How to remove the gnome panel?"
date: 2010-05-11
forum: Desktop Environments
---

### Post by True_Snake on 2010-05-11
Hello,

I was wondering if it's possible to remove the gnome panel,
I prefer the use of dock-lets and I don't have any use for the panel
but when I remove my panel with apt en reboot my computer
he seems to be unable to load gnome and I only get a terminal
(or KDE desktop when installed)
I didn't find another topic on this so I was wondering if it's possible
to remove and if, how to achieve it.

all reply greatly appreciated.

---

### Post by howefield on 2010-05-11
If you want rid of one panel, right click the offending panel and select Delete This Panel.

The second panel is harder to get rid of for obvious reasons... but should you want to, you could try this.

1. Press Alt + F2 keys together.
2. Type gconf-editor in the run box that pops up.
3. Click the Run button.
4. Navigate to Desktop > Gnome > Session > required_components
5. Right click on panel and select Edit Key.
6. Delete the value gnome-panel
7. OK your way back out.

You might need to log out/back in for it to take effect.

---

### Post by kanaqsasak on 2010-05-11
I do as you suggest.. because I just want to use Gnome-Do
but after that I can't restore the gnome panel.. and I can't open nautilus..
please help.. :(

---

### Post by howefield on 2010-05-11
> **kanaqsasak said:**
> but after that I can't restore the gnome panel.. and I can't open nautilus..(

Reverse the steps, only put the value back in instead of taking it out.

---

### Post by sakisds on 2010-05-11
As an alternate, you could apt-get install xfce4 and choose xfce over gnome. It will give you a basic desktop with no panels but i don't know how well gnome-do will work.

---

### Post by True_Snake on 2010-05-11
I've used gconf-editor, and after login out and back in
the panel is gone and my awn and gnome-do still works perfect

thanx

(going to mark this thread solved)

---

### Post by silvagroup on 2010-09-09
HELP !!!
Tried this but gnome-panel will not go away.
I even changed required-component to avant-window-manager and I still get the gnome-panel at top of the desktop !!!!!
Where else could they be hiding the settings?

---

### Post by ceverett on 2010-09-18
Same for me.  Gnome is starting to feel Like Windows!!!!!

---

