---
title: "Twinview Questions"
date: 2009-07-30
forum: Desktop Environments
---

### Post by Whisp3r on 2009-07-30
Hi everyone. The newbie-for-life here!

If I have two monitors, and NVidia's Twinview fired up (GTX260), is there anyway to extend the panels to my "other" monitor? I have panels on my left monitor, but not right. If I minimize something on the right side, I have no way to get it back.

Thanks!

---

### Post by wojox on 2009-07-30
I have the same set up and when I minimize from the right it goes draws down to the left bottom panel. How long have you had this set up?

---

### Post by Whisp3r on 2009-07-30
I've had it a couple of weeks. When I minimize on the right screen, it draws down like it's going to a tab on the left window panel. I just minimized a firefox window on that side, and now I can't get it back. If I move a window from the left monitor to the right, the tab on my bottom left panel disappears.

---

### Post by wojox on 2009-07-30
Ok open your nvidia x server settings and click on X Server Display Configuration. Then click on the left panel layout and see if the Make this the primary display for the x screen is checked.

---

### Post by Whisp3r on 2009-07-30
> **wojox said:**
> Ok open your nvidia x server settings and click on X Server Display Configuration. Then click on the left panel layout and see if the Make this the primary display for the x screen is checked.

Yep, left screen is marked primary display.

---

### Post by wojox on 2009-07-30
Ok Right-click on one of your bottom panel, select "Add to Panel", and try adding the "Window List". That should show you any minimized windows you have.

---

### Post by Whisp3r on 2009-07-30
I tried that. It just adds another set of window lists, duplicating the one I already have. It doesn't show any of the ones on the right monitor.

Edit; For kicks, I tried a "window menu" and it does show all my windows. So the problem lays in the window list. Hmm.

---

### Post by Whisp3r on 2009-07-30
Solved!

I deleted the whole left panel, then recreated it and added a window list. Now it shows both. Oh well, guess you just have to get rid of the first panel and replace it with a new one. Kind of like wives. :P

---

### Post by wojox on 2009-07-30
This is what I followed to set up my drivers:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

May help?

---

### Post by wojox on 2009-07-30
Good job. :D

---

