---
title: "Xfce Panel in LXDE?"
date: 2011-09-11
forum: Desktop Environments
---

### Post by XubuRoxMySox on 2011-09-11
Can it be done? I'd try it out myself but I have only one 'puter and it's mission-critical! I'm scared of messing it up like last time I tried mixing and matching stuff from different DEs.

Love LXDE's speed, but I also love that Xfce panel even better than a dock!

Thanks!

---

### Post by Linux_junkie on 2011-09-11
Check out lubuntu.net I'm sure it tells you how to xfce type panel on lxde.

---

### Post by kerry_s on 2011-09-11
> **XubuRoxMySox said:**
> Can it be done? I'd try it out myself but I have only one 'puter and it's mission-critical! I'm scared of messing it up like last time I tried mixing and matching stuff from different DEs.

Love LXDE's speed, but I also love that Xfce panel even better than a dock!

Thanks!

yes it can be done easily.

**gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart**

change:
**@lxpanel --profile Lubuntu**
to
**@xfce4-panel**

log out & back in

configure the panel. enjoy ;)

---

### Post by XubuRoxMySox on 2011-09-11
Thank you both!

The site demonstrates some wonderful capabilities of the LXpanel I hadn't noticed in my previous "flirtations" with LXDE. It looks absolutely delightful. LXDE was "under heavy development" when I played with it before (a year ago almost, wow), and somewhat buggy. The videos demonstrate big improvements! I wonder if I might just keep that sweet new LXDE panel. The only thing I would change is having that way cool Xfce weather applet on my LXDE panel. I'll try it!

And if it doesn't work, I'll simply use the Xfce panel in my LXDE.

Thank you both again, very much!

---

### Post by amjjawad on 2011-09-22
I'm more than HAPPY with ALL LXDE Components including LXPanel and the menu.

I have two Panels, just like the tutorial on Lubuntu's website. I'm sure you saw it.

---

### Post by Troop116rules on 2012-08-27
> **amjjawad said:**
> I'm more than HAPPY with ALL LXDE Components including LXPanel and the menu.

I have two Panels, just like the tutorial on Lubuntu's website. I'm sure you saw it.

Yes, but LXPanel doesn't support Gnome Applets...at all...even unofficially.

Network Manager is an exception. I hate that they call it an "Applet". The icon you see in the taskbar in LXDE is actually a program running in the system tray. Applets are attached to the panel for your desktop environment, where the system tray is a separate entity entirely. Hence, nm-applet (Network Manager applet) will run in most Desktop Environments like LXDE, XFCE, among others. (I think KDE has bugs with nm-applet)

xfce4-panel supports Gnome Applets officially. :D

---

### Post by vasa1 on 2012-08-27
necro?

---

