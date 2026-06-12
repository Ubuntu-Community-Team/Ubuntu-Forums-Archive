---
title: "synclient and horizontal edge scroll"
date: 2007-11-19
forum: Desktop Environments
---

### Post by barrack on 2007-11-19
Hey all, I recently upgraded to gutsy and one of the first things I noticed was that my horizontal edge scrolling was not working. I remember dealing with this before in feisty, so I quickly opened up a terminal and typed "synclient -l" to see the touchpad settings.
```

    VertEdgeScroll       = 1
    HorizEdgeScroll      = 0
```

So then I typed```
 sudo synclient HorizEdgeScroll=1

```

Then it worked! Hoorah!

BUT, whenever I reboot the machine, it goes back to zero.

What is the crucial (and hopefully simple) step that I am missing to make the horizontal scrolling work without me having to go edit the settings each time?

Thanks!

---

