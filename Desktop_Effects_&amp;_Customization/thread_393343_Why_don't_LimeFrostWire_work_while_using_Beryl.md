---
title: "Why don't Lime/FrostWire work while using Beryl?"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-03-25
I've successfully installed both Beryl and FrostWire on my computer, and although I know that FrostWire doesn't work while using Beryl (just gives me a gray window), I'm wondering if anyone actually knows why. And if so, is it possible to get it to work?
Switching back and forth between Metacity and Beryl gets annoying.

---

### Post by terdon on 2007-04-12
Adding this to your ~/.bashrc file should fix it```

alias frostwire='export AWT_TOOLKIT=MToolkit && frostwire'
```

---

