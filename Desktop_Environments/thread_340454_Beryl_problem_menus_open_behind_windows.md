---
title: "Beryl problem: menus open behind windows"
date: 2007-01-17
forum: Desktop Environments
---

### Post by kilou on 2007-01-17
Hi,

I'm on Ubuntu Edgy and I run Beryl 0.1.4 with AIGLX on an Intel i915G gpu. Most of the time everything works fine but sometime I have problems with Gnome panel menu, application menus and right click menus. For example if I have an openend maximized window and click on the Gnome panel menu, the menu opens but behind the window (so I cannot access it). One other symptom is if that menus within one particular application (or even in nautilus) do not get displayed. I assume it's just that they open but behind the window too for some reason. The same happens with right click menus not opening when right clicking on an icon in nautilus for example. This behaviour happen not only in nautilus but also in other applications such as OOffice.

To solve this I have to launch beryl-manager and reload the window manager (Beryl).

This sound like a Z ordering issue on menus. Any idea what is causing this and how I may solve this?

Thanks

---

### Post by eXisor on 2007-01-17
I don't think there's anything a user can do about the problem. I'm running 0.1.5 (trevino's svn builds), but it's happened with all the builds to date, albeit less frequently. i suggest you start beryl using the beryl-manager so you get the red diamond in the notification area, which then allows for a quick beryl reload whenever this happens.

It's an annoyance, but since beryl is still a beta, mayhap they'll get this sorted eventually. For a beta, it's pretty solid otherwise.

---

### Post by kilou on 2007-01-18
I just installed version 0.1.5 from Trevino's repositories and so far I didn't have any menu problem :) However do you know if it is possible to save the beryl configuration on version 0.1.5??? I can't find how to export the config to a file like it was possible to do with 0.1.4...

---

### Post by eXisor on 2007-01-18
Hmmm, I also can't find the export/import. Perhaps they'll put it back with the next update; they come pretty thick and fast.

---

### Post by naruto-kun on 2007-02-09
Ok I get a similar problem.  

I open a new window (of any kind) and it opens behind the current windows. 

It is a nuisance :(  This happens even before starting Beryl. 

Frustration is setting in...

---

### Post by PriceChild on 2007-02-09
Disable Focus Stealing Protection "FSP" on the first page of the settings manager

---

### Post by shareMenaPeace on 2007-02-09
I set it to LOW and it is fine ...

---

### Post by naruto-kun on 2007-02-09
Awesome

---

### Post by Snookered on 2007-02-23
> **PriceChild said:**
> Disable Focus Stealing Protection "FSP" on the first page of the settings manager

Thank you, PriceChild!

---

### Post by jparadis on 2007-04-11
Thanks! I have been wondering what setting to change to fix this problem.

jp

---

