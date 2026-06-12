---
title: "Preventing an application from showing in the unity launcher"
date: 2012-01-08
forum: Desktop Environments
---

### Post by I_can_see_the_light on 2012-01-08
I'm doing some experimenting with gnome-fallback session and the Unity2D-launcher. Unfortunately the gnome-panel gets an entry in the launcher like all other applications. That's maybe only a cosmetic issue but it's annoying nonetheless. 

Is it possible to "blacklist" an application from appearing in the launcher? Maybe editing the gnome-panel.desktop in some way? I have tried searching Google but haven't found a solution. Perhaps someone can shed some light? (And no, I can't see it right now :o )

---

### Post by Frogs Hair on 2012-01-08
Are you referring to the icon that appears while the application is open ?    The panel and the launcher appear separately in the dconf Editor . Though there is a white list option for the panel I see no blacklist for either .

---

### Post by I_can_see_the_light on 2012-01-08
> **Frogs Hair said:**
> Are you referring to the icon that appears while the application is open ?

Exactly. 

I haven't found anything in the dconf editor either to customise which applications are shown, that's why I thought that there might be some "magical" option to put in the .desktop items.

I actually wouldn't mind logging in to Unity 2D but because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/869196") things become a little bit annoying.

---

