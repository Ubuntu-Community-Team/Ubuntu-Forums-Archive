---
title: "All I got is a mousecursor!"
date: 2009-04-18
forum: General Help
---

### Post by olskar on 2009-04-18
Hi, when I boot, all I get is a mousecursor and a wallpaper. I can move the mousecursor but nothing else.

I can still access ctrl+alt+f1 terminal. Is there any logs I can check in on what happens? Anyone have an idea whatsoever? I've run out of ideas :(

---

### Post by justin_guerin on 2009-04-18
Check /var/log/Xorg.0.log and /var/log/messages.

Also check that you have a desktop environment (or at least a window manager) installed.

Does this happen before GDM comes up, or only after you log in?

---

### Post by aaronp on 2009-04-18
> **olskar said:**
> Hi, when I boot, all I get is a mousecursor and a wallpaper. I can move the mousecursor but nothing else.

I can still access ctrl+alt+f1 terminal. Is there any logs I can check in on what happens? Anyone have an idea whatsoever? I've run out of ideas :(

If this is happening after you log in then maybe you have inadvertently got rid of your panels. Are you able to start the gnome-panel from the terminal screen?

---

