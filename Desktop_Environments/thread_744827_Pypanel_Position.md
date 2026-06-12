---
title: "Pypanel Position"
date: 2008-04-04
forum: Desktop Environments
---

### Post by BluntBox on 2008-04-04
Howdy all, I have a small question about Pypanel for anyone that can answer it. I've seen many screenshots of Pypanel, where the panel has space on all sides, between it and the screen edges.

But for the life of me I can't find a property to get the 'long' edge to move away from the edge it is attached to.

---

### Post by chucky chuckaluck on 2008-04-04
if you'll look in your *.pypanelrc* file, you'll note a section called "panel spacing and location options". you should be able to get what you want by changing those values.

---

### Post by BluntBox on 2008-04-04
Currently my pypanelrc has this in the Panel Spacing and Location section:
```

P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 1888          # Panel width: 0 = Use full screen width
P_START         = 16            # Starting X coordinate of the panel
P_SPACER        = 6             # Spacing between panel objects
P_HEIGHT        = 19            # Panel height

```

I changed the Width and Start to get the bar to have the space between the ends and the edge of the screen, but none of the other values effect the 'long' side of the bar.

---

### Post by BluntBox on 2008-04-04
Well, I found the solution. Needed to apply a [patch](http://pastebin.ca/568668) to pypanel to add the ability.

---

### Post by BluntBox on 2008-04-14
Just my luck, need to use the patch again but pastebin.ca appears dead. Hoping someone that knows a valid link to the patch, or is able to attach it sees this thread.

---

### Post by urukrama on 2008-04-14
[That]("http://de.pastebin.ca/568668") link works for me.

---

