---
title: "PyPanel config question"
date: 2008-12-02
forum: Desktop Environments
---

### Post by Exershio on 2008-12-02
I've had pypanel set up for a bit now, and I noticed that "URGENT" messages dont cause the task to flash a certain color, like they do in Windows, GNOME, etc. For example, when you have a pidgin conversation minimized, and someone sends you a message, it should flash on the panel, to let you know you have a message to read.

Is there any way to replicate this behavior in pypanel? I have yet to figure it out.

---

### Post by Zorael on 2008-12-03
Are you running Compiz? Perhaps it's simply not passing urgent/demanding attention flags to pypanel. Try it with another window manager.

```
$ metacity --replace &    # GNOME
$ kwin --replace &        # KDE3, not sure about KDE4 - just disable effects
```

---

### Post by canistra on 2008-12-03
> **Exershio said:**
> I've had pypanel set up for a bit now, and I noticed that "URGENT" messages dont cause the task to flash a certain color, like they do in Windows, GNOME, etc. For example, when you have a pidgin conversation minimized, and someone sends you a message, it should flash on the panel, to let you know you have a message to read.

Is there any way to replicate this behavior in pypanel? I have yet to figure it out.

pypanel doesn't got such a function ...

---

### Post by Exershio on 2008-12-03
> **Zorael said:**
> Are you running Compiz? Perhaps it's simply not passing urgent/demanding attention flags to pypanel. Try it with another window manager.

```
$ metacity --replace &    # GNOME
$ kwin --replace &        # KDE3, not sure about KDE4 - just disable effects
```

I'm running openbox and pypanel. Pretty minimalistic system.

> **canistra said:**
> pypanel doesn't got such a function ...

Are you sure about this? If that's true, I'll have to find a new panel.

---

