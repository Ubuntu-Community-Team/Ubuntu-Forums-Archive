---
title: "What's so important to libweather-common?"
date: 2009-02-26
forum: General Help
---

### Post by siddartha on 2009-02-26
What's so important to libweather-common to link it to fast-user-switch-applet and gnome-panel? Tried yesteday to uninstall it as I don't need its functionality. Yea, libgweather1 is also in direct relationship, but that makes sense. Why gnome-panel depends on this library, which is quite large by the way.

---

### Post by dcstar on 2009-02-27
> **siddartha said:**
> What's so important to libweather-common to link it to fast-user-switch-applet and gnome-panel? Tried yesteday to uninstall it as I don't need its functionality. Yea, libgweather1 is also in direct relationship, but that makes sense. Why gnome-panel depends on this library, which is quite large by the way.

The same gnome-panel that has the Weather display built into it?, I wonder why......

---

### Post by sdennie on 2009-02-27
You can determine why this dependency is here with:

```

dpkg -L gnome-panel

```

In this case, it's because the gnome-panel comes with the clock applet and the clock applet has a weather component to it.  If you right click on the clock, and go to preferences, you can see where that is configured.

---

### Post by siddartha on 2009-02-28
But why that applet is built-in? I mean for each package they make it smaller and smaller than they link it to some huge set of packs. For such limited functionality sounds rather obscene to force the adition of about 25M extra.

---

