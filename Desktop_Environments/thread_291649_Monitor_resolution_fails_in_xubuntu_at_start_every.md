---
title: "Monitor resolution fails in xubuntu at start every time"
date: 2006-11-02
forum: Desktop Environments
---

### Post by lizardking on 2006-11-02
Hello everybody,
premised that I use Ubuntu approximately form 3 years, therefore I have one sure experience in matter. I have tried to install on a PC without great performance the  xubuntu 6.10 in order to facilitate it. The PC is 500 Mhz Celeron with 128 MB ram and 4 Gb of HD.
I have tried launch the LIVE cd of xubuntu 6,10, the last version. And there it begins the problems. **Perhaps until the usplash is staring all ok, the resolution seems ok , but just  too much high one; at the moment that it loads GDM arrive the matter: obviously the configured resolution is too much high, for being supported from the graphical card even if the monitor resists it. Therefore for this reason the mouse has a double pointer and the monitor not succeeded to work.** So I have decided to install the alternated CD and then all goes ok….**When I arrive to log in I get the same problem.** So I make: I logged in a rescue terminal on hand and I give a beautiful one Code: 
```
sudo dpkg-reconfigure xserver-xorg
```

** I configure all with the just resolution, return on serveur X and .All was fine. Right resolution. I believed of having resolved when… reset the PC, usplash goes, i get GDM and… the usual problem, mistaken resolution. So I have gone in: **

```
/boot/grub/menu.lst
```

 and I have added the line **vga=791** to kernel so the splash leaves with the corrected resolution 1024x768.

Also this is not served to nothing. I do not have more ideas and I do not know how to fixing this thing. An idea is to remove the usplash because I think that the responsable of the damage is it.** I cannot configure X server every time that I want myself to be log in eh…**

some help?

---

