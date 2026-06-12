---
title: "Wayland Compositor / X11 Compositor"
date: 2023-09-26
forum: Desktop Environments
---

### Post by Shibblet on 2023-09-26
Been using Kubuntu for quite some time now, and finally decided to give Wayland a try.  Currently running 23.04.  From a Kubuntu perspective, it doesn't really seem to change much on the surface...

Anyway, I play Skyrim on Steam, and I have noticed that I get a better frame rate when I disable the X11 compositor.  However, there doesn't seem to be any way to disable the Wayland Desktop Compositor before I play Skyrim... so I some choppy and lower frame rates from time to time.

I have an AMD 5900HX along with a RX6600M, and I get 60fps (constant) when I run in X11.  Wayland, I get (average) 45fps, sometimes 60, and sometimes 30 depending on the area I am in.  Dungeons are always 60, outdoor areas can be as low as 30.  So, in no way is the game "unplayable," (to me anyway), but I know the performance is available.

Any ideas?

---

### Post by Holger_Gehrke on 2023-09-28
That a program responsible for - mostly - eye-candy on X11 and a central part of Wayland are both named compositor is misleading. The Wayland compositor is the part of Wayland that collects images from the applications and assembles them into one picture - the desktop. So basically: no compositor - no Wayland. The uneven frame rate between X11 and Wayland is probably down to decades of optimization in X11 versus a system which still is very much in flux in Wayland.

Holger

---

### Post by Shibblet on 2023-09-28
> **Holger_Gehrke said:**
> That a program responsible for - mostly - eye-candy on X11 and a central part of Wayland are both named compositor is misleading. The Wayland compositor is the part of Wayland that collects images from the applications and assembles them into one picture - the desktop. So basically: no compositor - no Wayland. The uneven frame rate between X11 and Wayland is probably down to decades of optimization in X11 versus a system which still is very much in flux in Wayland.

Holger

So... better to game on X11?

---

### Post by Holger_Gehrke on 2023-09-28
> **Shibblet said:**
> So... better to game on X11?

For the short term, yes. In the long run Wayland will hopefully get better and X11 will probably stagnate since most of the Wayland devs used to work on X11 and there's very few people working on it now. You also might want to check whether your game runs under xwayland - the Wayland X11 compatibility layer. If that's the case, it might be a while until Steam - or whatever Steam uses to run games (Proton is what it's called, I think; somewhat similar to Wine) - switches over to Wayland.

In the long run X11 will become a system used in very specific circumstances where Wayland can't be used, most probably complex semi-automated workflows which are hard to do on Wayland since X11 automation tools rely on X11's relative lack of security features that protect apps from one another - which was one of the reasons to create a new protocol along with the existence of many features in X11 that modern programs don't use, for example drawing of graphical primitives or text rendering. Modern apps do these things through GTK or QT which don't rely on X11 to do these things for them.

Holger

---

