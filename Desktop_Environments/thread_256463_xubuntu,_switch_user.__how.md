---
title: "xubuntu, switch user.  how?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by StickyStyle on 2006-09-13
In the regular gnome version of ubuntu there is a nice menu item on the shutdown/logout screen for switching users, it seems to be missing in xubuntu (at least on my install).

Does this handy button exist? If so how do i add it back?

Also, is there a way to have the computer drop back to gdm when the screensaver kicks in so it is just back at the login screen?  That way if someone else wants to login after the computer has been sitting idle they just have to...login, rather than hitting the elusive "switch user" button.  Both WinXP and OS X can do this and i would be alarmed if nothing of the sort existed in the linux world.

---

### Post by MattJ100 on 2006-09-16
Yep, the want of a fast user switching system is what tipped me over the edge, and into linux. I also have Xubuntu, because I like things light, and I already have it on another PC.

I am also in want of this button, however...

1) When the screensaver is active, move the mouse, and click 'New login' instead of entering a password.

2) Add an action button to the xfce panel, and make it 'Lock screen', this starts the screensaver, and you can use method 1.

3) I was browsing the forums the other day for this problem, and found just what I needed. There is a command, that you can create a launcher from. Unfortunaely I've had ATI driver problems, and reinstalled several times. Now for the life of me, I can't find what this command was. I'm here searching now :)

It started with gdm... (and by it's name, I never would have guessed what it did)

If I find it, I'll post back, if anyone else knows what it is, please enlighten us :)

---

### Post by MattJ100 on 2006-09-16
Excellent, I found it :D

Just run: gdmflexiserver

Add that as a launcher command, and you're away! :)

---

### Post by StickyStyle on 2006-09-18
Totaly sweet! thanks. :-D

---

### Post by StickyStyle on 2006-12-29
Thought i would bring this post back just so i can update and document what i did in case anyone else wants the same functionality in xubuntu.
apt-get install fast-user-switch-applet xfce4-xfapplet-plugin

The xfce4-xfapplet-plugin lets you run gnome applets in xfce, and fast-user-switch-applet is the applet that does the switching.  Just add xfce4-applet-plugin to your xfce panel just as any other applet, then you will see a list of installed gnome applets to add.  Quite a nice solution.

---

### Post by silmaril8n on 2007-02-18
Oddly enough I was using the "gdmflexiserver" for a few days and now, for an unknown reason, it isn't working. So, I tried the Gnome applet solution and that doesn't work either. I just end up with the Gnome logo in my task bar and nothing happens when I click it. When I run "gdmflexiserver" in my console I get no errors, but it just hangs there until I ctrl-c it.

---

