---
title: "How to fix position of icons in system tray?"
date: 2010-07-07
forum: Desktop Environments
---

### Post by vangop on 2010-07-07
Hi!
I removed the bottom panel and killed gnome-panel process. After that the icons are shown in random order on the panel. 
The clock is sometimes in the middle, sometimes at the end. This is very annoying :) I locked it to the panel, but it keeps moving randomly after restart. And I can't move it after the panel is loaded.
Any suggestions?

---

### Post by SmokeyThePanda on 2010-07-07
I believe you can simply restore the default gnome panels, then edit them to your liking once more. 

```
sudo debconf gnome-panel
```

That should work..If not, come back. :)

---

### Post by vangop on 2010-07-08
Hi Smoky!
I tried the command, and the panels did reappear, but for some reason the panel was also messed up, the clock was in between of the icons... And after I closed the terminal, they disappeared and my layout was restored back :) 
I dug this in gconf-editor under /apps/panel
I just tried to correct the indexes manually. It is a very easy structure, just listing applets/objects and you can tune the index and specify if it should be counted from left or right panel border.
For some reason counting from right didn't work, so I just had to assign a large number to clock applet, and the rest worked.

I just don't understand the difference between notificator applet and notification area. I have both of them. Can I remove 1? 
Another thing is that mail icon pops up a menu on Super<M> while it has to be a negative screen on this key. Can I disable this or remove the mail icon somehow?

---

