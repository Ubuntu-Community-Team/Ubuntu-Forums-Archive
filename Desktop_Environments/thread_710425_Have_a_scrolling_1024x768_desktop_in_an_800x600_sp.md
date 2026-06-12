---
title: "Have a scrolling 1024x768 desktop in an 800x600 space."
date: 2008-02-28
forum: Desktop Environments
---

### Post by Gen2ly on 2008-02-28
I have an issue with the monitor size on my laptop that I'm thinking is something that I can fix but have no idea how to do it. :-|

The deal is I have a monitor that can only display up to 800x600 but I just installed a program that's requiring 1024x768.  I need this program too.  

This is something I've seen previously yet no idea on what to do to do this.  Has someone done this and know how?  Thanks in advance.

---

### Post by Gen2ly on 2008-02-28
nm, i just found out - man xorg.conf (rolls--eyes)
```

        SubSection "Display"
                Depth           16
                Modes           "800x600" "640x480"
        Virtual     1024 768
        EndSubSection
```

---

