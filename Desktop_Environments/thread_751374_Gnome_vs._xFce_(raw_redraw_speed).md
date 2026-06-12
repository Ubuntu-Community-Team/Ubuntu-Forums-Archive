---
title: "Gnome vs. xFce (raw redraw speed)"
date: 2008-04-10
forum: Desktop Environments
---

### Post by crstn_udrea on 2008-04-10
My linux system is a 1300Mhz Duron (morgan core - 64 kib L2 cache) with 768 MB DDR (PC 1600). KDE was always (and still is) a resource hog. However I was quite stunned to see that Ubuntu (GNOME) runs very slow. Not comparing to windows here. (I do realize there's about 5 daemons and the X server in between the commands and the actual drawing) but windows are actually trailing on the screen. I've used various other distros (with GNOME) and although it was slow as well, there was no actual trailing.

Anyway, right now I'm running xubuntu 7.04. It's quite stable, and fast but apps like openOffice, GIMP, inkscape, etc. have (naturally) some bugs when rendering. I would go back to ubuntu but the redraw sped is a real killer. I could just recompile GNOME and get a bit of extra performance but that would take ... TOO LONG

Any suggestions on why this is happening (with possible solutions?). Last the ubuntu I installed was also 7.04.

---

### Post by Aztek on 2008-04-10
I wouldn't expect there to be performance issues with Gnome on that setup, so maybe something else is wrong. Is there any reason you can't try a fresh install of Gutsy (7.10) to see if that fixes your problem?

I'm surprised that XFCE is having problems rendering things since version 4 uses GTK.

What video card are you running?

---

### Post by cometa2k7 on 2008-04-10
Strange problem.

XFCE seems to work well on lower powered computers. But when I used a 900MHz processor in my old computer, I could run any of the desktop environments, in fact I tested every one that I could.

Isn't XFCE Gnome based anyway?

Could it be a problem with your graphics card? What level of desktop effects are you using in GNOME?

---

### Post by crstn_udrea on 2008-04-10
No fading of menus, no shadowing. The video card is an integrated ProSavage DDR (64MB share).

XFCE doesn't have any other problems except redraw issues (mostly trailing) in gtk+ based apps (and openoffice)

---

### Post by tighem on 2008-04-10
I just installed Xubuntu desktop the other day and would switch over in a minute if it supported full set of network sharing. It's much faster than gnome.

---

### Post by cometa2k7 on 2008-04-11
> **tighem said:**
> I just installed Xubuntu desktop the other day and would switch over in a minute if it supported full set of network sharing. It's much faster than gnome.

Yeah, I love XFCE, but I'm a bit too settled in GNOME now, I might switch back when I upgrade to 8.04, I don't much care for betas. I will probably download both Ubuntu and Xubuntu, and see what I can get Xubuntu to look like; I like my current configuration.

---

