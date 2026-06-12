---
title: "Weird thing happens when i click apps on panel"
date: 2007-03-22
forum: Desktop Effects &amp; Customization
---

### Post by gigermunit on 2007-03-22
When i click things on my panel i get this weird glitchy looking thing whats up with that?

---

### Post by mcduck on 2007-03-23
> **gigermunit said:**
> When i click things on my panel i get this weird glitchy looking thing whats up with that?
Are you talking about the wireframe animation? Some Gnome developers must think that it looks nice :rolleyes: 

Anyway, here's how to disable it:

1. hit Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global and disable 'enable_animations'

If you are using Metacity (the default window manager in Gnome) you might also want to change these:

4. in apps/metacity/general enable 'reduced_resources'
5. in desktop/gnome/interface enable 'accessibility'

---

### Post by highneko on 2007-03-23
An easier way of doing what mcduck suggested is:
```
gconftool-2 -s /apps/metacity/general/reduced_resources --type=bool true
gconftool-2 -s /apps/panel/global/enable_animations --type=bool false
gconftool-2 -s /desktop/gnome/interface/accessibility --type=bool true
```

---

### Post by gigermunit on 2007-03-23
it's more of the entire screen glitching out

---

