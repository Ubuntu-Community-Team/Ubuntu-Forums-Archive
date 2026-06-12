---
title: "How do I temporarily disable Compiz in Oneiric?"
date: 2011-10-30
forum: Desktop Environments
---

### Post by Diskdoc on 2011-10-30
Games in Wine when using fglrx. I need to disable Compiz temporarily, how? I used to do this with a sort of Compiz-applet (which now runs but doesn't show). In Natty I logged out, chose Ubuntu Classic and used the applet to disable Compiz.

I don't see the right option for this in CCSM. How do we disable Compiz smoothly in Oneiric?

(edit)

That was easy. Just choose Unity 2D instead!

---

### Post by 3Miro on 2011-10-30
Do you still have an issue? If not please mark the thread as solved.

11.04 comes with Gnome 2 and Unity, under classic interface you are looking at Gnome 2 + Compiz and you can select Fusion Icon to temporarily replace Compiz with Metacity.

Ubuntu 11.10 comes with Untiy 3D (Compiz) and Gnome 3, hence Fusion Icon doesn't work (i.e. switching back to Metacity isn't trivial). Unity 2D disables 3D effects (and Compiz) and will probably be better for games. You can also install Gnome-session-fallback, which will give you a Gnome 2-like interface with Gnome 3 ports of Metacity and Gnome panel (although you can't easily switch between Unity and Gnome-fallback).

You can try to use Compiz + wine, in CCSM and workaround options, there is an option to select "legacy fullscreen support", which should help some of the wine games. I don't know if it will work for you.

---

### Post by ingeva on 2011-10-31
> **Diskdoc said:**
> 
That was easy. Just choose Unity 2D instead!
Eh....  HOW do you choose Unity 2D?

---

### Post by mcduck on 2011-10-31
> **ingeva said:**
> Eh....  HOW do you choose Unity 2D?

From the dropdown box in the login screen (After selecting your user, but before entering your password).

---

### Post by ingeva on 2011-10-31
> **mcduck said:**
> From the dropdown box in the login screen (After selecting your user, but before entering your password).
I may not remember exactly since I have removed the installation, but I don't think that helped any.

---

### Post by mcduck on 2011-10-31
> **ingeva said:**
> I may not remember exactly since I have removed the installation, but I don't think that helped any.

Well, that's the only way you can get a desktop without Compiz (you can't disable it when running normal Unity session as Unity is a compiz plugin). And yes, it definitely does work...

---

