---
title: "X resolution keeps swtiching"
date: 2010-12-26
forum: Desktop Environments
---

### Post by darkcoffee on 2010-12-26
Barebones installation.  Manually start x with 'startx'.  For some weird reason, the resolution randomly sets to either 1024x768 or 800x600.  How do I permanently set a resolution?

---

### Post by mikewhatever on 2010-12-26
Putting it into xorg.conf would be one way of doing it. You may need to generate an xorg file first with 
'Xorg -configure'.

---

