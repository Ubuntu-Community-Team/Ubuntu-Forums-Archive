---
title: "Fluxbox appears bare"
date: 2007-05-20
forum: Desktop Environments
---

### Post by B-Con on 2007-05-20
I'm using Ubuntu 7.04 and figured I'd give Fluxbox a try. I installed it via "apt-get install fluxbox" and started a session using it, but I'm somewhat confused... it looks blank. There's nothing on my desktop, no configuration menus or anything. If I start nautilus then my desktop appears but I lose my ability to right-click and get the comples fluxbox menu system and it's basically like using Gnome only with the fluxbox border style.

What am I missing... Do I need to start some program or something?

---

### Post by kerry_s on 2007-05-20
in a terminal or ctrl+alt+F1 run> sudo update-menus
That will give you a default menu. nautulius has to be run with the -no-desktop option.

---

### Post by RedSquirrel on 2007-05-20
I think it's 

```
nautilus --no-desktop
```but check the manpage for nautilus to be sure of the spelling of the options:

```
man nautilus
```I think the menu generators for Fluxbox make it something similar to:

```
nautilus --no-desktop --browser
```The links in my sig might help you to make a prettier Fluxbox and make a fancy menu. Have fun. :)

---

### Post by B-Con on 2007-06-09
Am I supposed to be able to see my normal desktop icons when I switch over to Fluxbox?

---

### Post by ugm6hr on 2007-06-09
> **B-Con said:**
> Am I supposed to be able to see my normal desktop icons when I switch over to Fluxbox?

I'm currently experimenting with fluxbox / Fluxbuntu, so am certainly no expert.  

But fluxbox doesn't have a desktop manager built in, so can't have any icons on the desktop.  iDesk accomplishes this very simply in fluxbox (haven't tried - just read about it).  Fluxbuntu uses ROX (instead of nautilus to do it.  

As for how to transfer icons from GNOME to fluxbox automatically - I have no idea.

---

### Post by B-Con on 2007-06-09
Ah, thanks. Wasn't aware of that minor detail. :-P

---

