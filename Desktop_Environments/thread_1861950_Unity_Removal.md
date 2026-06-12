---
title: "Unity Removal"
date: 2011-10-16
forum: Desktop Environments
---

### Post by KBD47 on 2011-10-16
I would like to either completely remove Unity or have it so that I boot directly into Gnome without having to stop at the log in page. Is it possible to remove Unity, or just auto log into Gnome?
  Unity has gone buggy on me and will not let me add apps to the launcher, or rather it does but now they won't stay. 
KBD47

---

### Post by mcduck on 2011-10-16
Unity *is* Gnome. ;)

Assuming you mean you want to automatically log in to *Gnome Shell*, this should help: [http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html]("http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html")

---

### Post by KBD47 on 2011-10-16
Thanks!

---

### Post by glennric on 2011-10-16
mcduck:  That is not true.  Unity is not gnome.  Unity is a separate application and is not even developed by the same people.  Unity is designed to be a replacement for the gnome-shell, and is specifically designed for Ubuntu.

KBD47:  You can use Gnome on Ubuntu without Unity.  Just install the gnome-panel package and then select the "Gnome Classic" session at login.  Alternatively, you can install the gnome-shell package and then select the "Gnome" session at login if you want to use Gnome 3.  Any of the other sessions are really using the Gnome 3 fallback session to make things look like Gnome 2.  Even the Unity sessions are using the Gnome 2 fallback mode.

---

### Post by mcduck on 2011-10-16
> **glennric said:**
> mcduck:  That is not true.  Unity is not gnome.  Unity is a separate application and is not even developed by the same people.  Unity is designed to be a replacement for the gnome-shell, and is specifically designed for Ubuntu.

KBD47:  You can use Gnome on Ubuntu without Unity.  Just install the gnome-panel package and then select the "Gnome Classic" session at login.  Alternatively, you can install the gnome-shell package and then select the "Gnome" session at login if you want to use Gnome 3.  Any of the other sessions are really using the Gnome 3 fallback session to make things look like Gnome 2.  Even the Unity sessions are using the Gnome 2 fallback mode.

Well, what I meant is that the Unity session of Ubuntu is running on top of Gnome, so when you are using Unity you are using Gnome as well.

So you can't switch between Unity and Gnome, but you can switch between Unity and Gnome Shell. In both cases you are using Gnome 3 as your desktop environment.

---

