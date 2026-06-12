---
title: "Missing Unity Right-Top Logoff/Shutdown Button"
date: 2012-04-01
forum: Desktop Environments
---

### Post by ReptilianShadow on 2012-04-01
Not sure how, but the "Power Button" in the top right corner disappeared. (Default Unity Session)

Any idea on how to get it back?

I noticed it was missing after I installed openbox and xfce4, but I wouldn't guess those be the issue.

I'm running Ubuntu 11.10 64 bit.

---

### Post by iiz on 2012-04-01
Alt+(Right Click) should bring up the panel configuration menu. From there you can add things to the panel, remove items, delete the entire panel, and configure the panel properties.

---

### Post by Frogs Hair on 2012-04-01
Try the following because the right click option doesn't  apply to Unity.

```
unity --reset
```

---

### Post by grahammechanical on 2012-04-01
You should also see a Shutdown icon in the file lens in the Dash. There should also be one Log out and Re-start. It does not solve the problem but it keeps the system usable.

you say

> I noticed it was missing after I installed openbox and xfce4, but I wouldn't guess those be the issue.

I would guess exactly that. Ubuntu uses either Compiz window manager with the Unity user interface or the Metacity window manager with the Unity user interface. And you have brought in two different window managers.

Regards.

---

### Post by pinguinhood on 2012-04-02
I have the same problem even if I didn't install additional windows manager. Here is my desktop screenshot.
[IMG]http://db.tt/zatmY5A6[/IMG]
As you can see, both user menu and Logoff/Shutdown Button are missing.
I tried unity --reset with no luck. I also tried to reinstall all unity* package but with no changes.

Any help would be appreciated!

---

### Post by greg.dean on 2012-05-08
> **Frogs Hair said:**
> Try the following because the right click option doesn't  apply to Unity.

```
unity --reset
```
Thank you.

---

