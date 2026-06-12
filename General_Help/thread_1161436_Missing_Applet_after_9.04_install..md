---
title: "Missing Applet after 9.04 install."
date: 2009-05-16
forum: General Help
---

### Post by macey on 2009-05-16
Hello,
on 8.04 there used to be an applet (can't remember what called) that I used to have on my top panel that used to be a 'roll-up' of search functions. You just clicked on the icon and a window opened up. Type within the window, & search results appeared as you typed. The applet was configurable, so you could get it to use tracker, google, the web etc. Even the calculator! Anyway, can't find it now.
Anyone know I can re-install? It's no longer in the 'Add To Panel' list.
Thanks.

---

### Post by soro2005 on 2009-05-16
It's called Deskbar. If it's not in the "Add to Panel" list, search for deskbar applet in synaptic.

---

### Post by macey on 2009-05-16
> **soro2005 said:**
> It's called Deskbar. If it's not in the "Add to Panel" list, search for deskbar applet in synaptic.

Ok, thanks. I've installed it via sudo apt-get install deskbar-applet.
Now, how can I get it onto my panel? I'ts still not in the 'Add To Panel' list.

Thanks.

---

### Post by Mirge on 2009-05-16
Application Launcher or Custom Application Launcher (Add to Panel) I would think? Try that out & let us know if that works :)

---

### Post by soro2005 on 2009-05-16
> **macey said:**
> Ok, thanks. I've installed it via sudo apt-get install deskbar-applet.
Now, how can I get it onto my panel? I'ts still not in the 'Add To Panel' list.

Thanks.

Hmm, weird. Perhaps log out and log in?

---

### Post by macey on 2009-05-16
> **Mirge said:**
> Application Launcher or Custom Application Launcher (Add to Panel) I would think? Try that out & let us know if that works :)

'fraid not as 'desktop-applet' is not recognised as a 'command'
even though installed.

---

### Post by macey on 2009-05-16
> **macey said:**
> 'fraid not as 'desktop-applet' is not recognised as a 'command'
even though installed.

Cracked it. Found out where installed & run from directory. Added path to startup command.

---

