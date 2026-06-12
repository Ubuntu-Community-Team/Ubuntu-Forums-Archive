---
title: "qtcurve: Affects GNOME apps when not logged into KDE"
date: 2013-08-22
forum: Desktop Environments
---

### Post by jlacroix on 2013-08-22
I recently installed KDE as a secondary desktop environment (not kubuntu-desktop, but just the bare-minimal KDE packages) and I also installed qtcurve so that GTK applications won't look stupid in KDE. That works fine, but when I'm NOT logged into KDE, all the GTK apps (Firefox, Banshee, etc) are still set to look like KDE. 

Is there any way to make the qtcurve settings in KDE take affect ONLY while logged into KDE?

---

### Post by bra|10n on 2013-08-23
Maybe you could have separate gtkrc config's set to load for each d/e? 
Perhaps sym linked to the original files ?

---

### Post by jlacroix on 2013-08-23
> **bra|10n said:**
> Maybe you could have separate gtkrc config's set to load for each d/e? 
Perhaps sym linked to the original files ?
Thanks for the reply, but I give up. I am under the impression that there is no possible way to have two desktop environments installed without the settings from one affecting the other. :(

---

### Post by Erik1984 on 2013-08-24
I noticed that as well when I installed ubuntu-desktop on my kubuntu install once. Unfortunately I don't know how to fix this, but I do support you conclusion: In general it's better to not mix desktop environments ;)

---

### Post by jlacroix on 2013-08-24
I wonder if maybe I should submit a bug against the qtcurve package?

---

### Post by bra|10n on 2013-08-24
> **jlacroix said:**
> I wonder if maybe I should submit a bug against the qtcurve package?

I wouldn't think so...
Both desktops environments happen to be reading the same .gtk*rc files without any problem. 
IMO your issue is that you need two sets of these, one for each environment.

While I've never done it, I see no reason why a couple of scripts with the required parameters set to load on startup in KDE and linked to the original files wouldn't work.

---

