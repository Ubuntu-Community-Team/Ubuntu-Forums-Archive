---
title: "gnome panel applets conquer new territories"
date: 2008-05-14
forum: Desktop Environments
---

### Post by Lobinho on 2008-05-14
Hi all,

I'm just wondering if it's possible to use some of the gnome panel applets outside of a gnome panel.  I.e., use the uim, notification area, network manager in awn or fluxbox or something.

I just started using awn and would like to try using it without any gnome panels, but still have the same functionality.  The awn notification area applet doesn't seem to be working for me, and I don't know how to add the uim to awn.

Also, I'd like to try using fluxbox, but as a total noob am sort of lost moving outside of familiar gnome menus, panels, etc.  I'm sure there must be cli commands for each of these applets, but what are they called and can they be incorporated into awn or the fluxbox slit?

Thanks!

---

### Post by RAOF on 2008-05-14
No, they can't (in general) be used outside the GNOME panel.  The panel applets tend to be intimately associated with the gnome-panel process.

---

### Post by Lobinho on 2008-05-14
Hmm, ok.  That's a little disappointing, but thanks for the info.

I feel like I've used the nm-applet for wireless networking in fluxbox before.  Is that not specifically associated with gnome panel or just an exception?

---

### Post by RAOF on 2008-05-14
nm-applet isn't actually a panel applet.  It's a program which displays a notification icon, and as such it can be used anywhere with a notification applet (GNOME, XFCE, KDE, etc all have notification area applets).

---

### Post by moonbeam on 2008-05-14
> **Lobinho said:**
> Hi all,

I just started using awn and would like to try using it without any gnome panels, but still have the same functionality.  The awn notification area applet doesn't seem to be working for me, and I don't know how to add the uim to awn.


In general awn devs currently recommend using stalonetray... with the proper configuration it visually complements awn.  Alternately a fair number of people use trayer which can be similarly configured.  

To be clear:  both trayer and stalonetray are separate apps from awn and will not run in the bar (normally they are placed in a bottom corner).

---

