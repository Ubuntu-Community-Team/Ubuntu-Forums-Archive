---
title: "Undock Gnome Panel?"
date: 2006-12-24
forum: Desktop Environments
---

### Post by jd_k on 2006-12-24
How do I undock the gnome panel? That is, how do I alter the settings in such a way that windows can be maximized over it? When I press "maximize" on a window, I want that window to then cover the *entire* screen, not all but the gnome panel(s).

(Sorry for the repetition, but there could be confusion.)

It has to be a simple setting in a figuration file somewhere, but I can't for the life of me figure it out.

Thank you,
~Joshua

---

### Post by dbbolton on 2006-12-24
well, it sounds to me like you should ditch the gnome panel and give gdesklets a try :)

---

### Post by jd_k on 2006-12-25
I have spent the last week coding/tweaking some gdesklets for a custom setup that is suited to my needs. I have a desklet for the tray, the pager, etc. There are two things that I am missing: (1) A menu-style launcher, which gnome-panel provides but I can't figure out how to embed in a desklet, and (2) the "logout" button on gnome-panel. I was more or less planning on keeping gnome-panel around for those reasons, but obviously don't need it continually pushing my programs out of the way.

If you have a different way to accomplish those tasks, I'm all ears. I found a menu-style launcher program that wouldn't compile on my system (perl or python conflicts of some sort; I have no experience or skills sorting out dependency issues). I was/am happy with my fluxbox menu, but am not sure how to (a) use that stand-alone, and (b) use that with nautilus managing the desktop (don't make fun of me; I like it at the moment). I understand that the "logout" button could be replaced by two launchers (one that would log out of gnome and another that would "gksu poweroff" or something like that), but -- and call me silly -- I like the gnome function better. I think it's linked to the gnome-powersaver somehow, but I couldn't find any documentation on it.

---

### Post by jd_k on 2006-12-25
Well, I found out how to set up launchers for the "lock screen" (although I don't like gnome-screensaver, so I'm using xlock instead) and the "logout" functions (the latter is actually operated by gnome-session-save; the specific call is "gnome-session-save --kill"). I am still looking for a way to call the menu (or an alternate menu).

---

