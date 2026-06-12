---
title: "Changing clock to 24 hours"
date: 2008-03-07
forum: Desktop Environments
---

### Post by mikeb on 2008-03-07
Setting up Ubuntu, although I put my location in Europe and synced to a European time server, the menu clock still display AM and PM. I have looked through preferences and can find no place to change this.

Is it possible to change? If so, how?

Thanks.

---

### Post by Het Irv on 2008-03-07
You Right clicked the clock, when to Preferences and did not see the Drop down box for 12/24 time? Thats Weird.  I am not sure what to tell you.  You might have corrupted Gnome settings.

---

### Post by mikeb on 2008-03-07
> **Het Irv said:**
> You Right clicked the clock, when to Preferences and did not see the Drop down box for 12/24 time? Thats Weird.  I am not sure what to tell you.  You might have corrupted Gnome settings.

No, I don't see that. That is very annoying that I will have to reinstall, but I don't see any other choice.

---

### Post by unutbu on 2008-03-07
Before you re-install, maybe someone knows which package provides the panel? taskbar? at the top of the screen. gnome-panel?

If gnome-panel is correct, then you could try

```

dpkg-reconfigure gnome-panel

```

---

### Post by mikeb on 2008-03-07
> **unutbu said:**
> Before you re-install, maybe someone knows which package provides the panel? taskbar? at the top of the screen. gnome-panel?

If gnome-panel is correct, then you could try

```

dpkg-reconfigure gnome-panel

```

Many thanks! I'll try that.

---

