---
title: "Questions about Window Managers"
date: 2009-04-28
forum: General Help
---

### Post by jacatone on 2009-04-28
I'm using Ubuntu 8.10 and from what I've read it uses the Gnome desktop environment and the Compiz window manager, or does it use the Metacity WM? Also, what WM does Xubuntu use? 

If I go to [www.gnome-look.org](www.gnome-look.org) what would I look under for different themes? Thanks.

---

### Post by 3Miro on 2009-04-28
Gnome could use either Compiz or Metacity. Compiz provides cool effects, but requires 3D graphics card (for Nvidia and ATi it also requires the proprietary drivers). Metacity is basic but work with almost no resources.

Xubuntu uses Xfe, look it up. I have never used Xfe.

---

### Post by Slim Odds on 2009-04-28
> **jacatone said:**
> I'm using Ubuntu 8.10 and from what I've read it uses the Gnome desktop environment and the Compiz window manager, or does it use the Metacity WM?

Compiz is not really window manager, it's a graphic interface framework. It defaults to using the Metacity WM. There is also Emerald (which looks nicer, but freezes my system sometimes).

Not sure about Xubuntu.

---

### Post by mb_webguy on 2009-04-28
The Xfce desktop environmnet (used by Xubuntu) uses the Xfwm4 window manager.

While Metacity itself is a window manager, the Compiz window manager can use Metacity as its window decorator.  It could also use the Emerald decorator.

I believe the Gnome by default uses Metacity as its window manager.  Ubuntu, however, uses Compiz as Gnome's window manager, but uses Metacity (or more specifically the GTK Window Decorator used by Metacity) as the default window decorator.

---

