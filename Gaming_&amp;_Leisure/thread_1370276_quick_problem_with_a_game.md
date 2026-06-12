---
title: "quick problem with a game"
date: 2010-01-02
forum: Gaming &amp; Leisure
---

### Post by Firch on 2010-01-02
I don't know if this is the correct forum but here we go...

I installed Pente on my computer recently and it says that it is installed on my computer when I search for the file. It does not, however, show up in applications/games where it says it is when I check the ReadMe file. any help???? I've installed other things before and after this game and have had no problems. I'm wondering why this one game is a problem.

---

### Post by tommcd on 2010-01-02
How did you install Pente? Pente is present in the Ubuntu 9.10 repos:
[http://packages.ubuntu.com/search?keywords=pente&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=pente&searchon=names&suite=karmic&section=all)
Did you install Pente from the Ubuntu repos? Or did you install it some other way?
Try running "pente" from the terminal (without the quotes) and see if the game launches. If you get errors when you do this, post them here.

BTW, it seems that you can play Pente online without installing anything:
[http://www.pente.net/](http://www.pente.net/)
[http://pente.org/](http://pente.org/)
Hmm, I never heard of this game before.

---

### Post by Firch on 2010-01-03
I got it from the software center. It runs via the terminal and I can locate the file fine. That is just kind of annoying whenever I wanna run it I have to go through the terminal. I was wondering if there was maybe something I'd have to change to get the icon to appear somewhere either on the desktop or usr/apps/games.

Pente is a pretty easy game to pick up but it's really hard to be good at, much like working with Ubuntu.

---

### Post by tommcd on 2010-01-03
> **Firch said:**
> I got it from the software center. It runs via the terminal and I can locate the file fine. That is just kind of annoying whenever I wanna run it I have to go through the terminal. I was wondering if there was maybe something I'd have to change to get the icon to appear somewhere either on the desktop or usr/apps/games.

Try right-clicking on the Applications menu on the top panel and choose "edit menus". Then navigate to the games section of the menu. See if Pente is there in the list. If it is, then put a check next to it and it should show up in the menu.
Sometimes you need to first run an application from the terminal, then logout and log back in again, or reboot in order for for the app to show up in the menu. The Epiphany web browser always does this when I install it for some reason. So try editing the menu, and then try rebooting to see if Pente will show itself in the menu.

If that does not work, then open a nautilus file manager window and navigate to where the executable for Pente is. It is likely under /usr/bin, /usr/games, or possibly /usr/local/games. When you find the executable file for Pente, simply right-click on it and choose "send to desktop" or "create shortcut" or whatever it says. This should put a launcher for Pente on the desktop.

---

