---
title: "Problem with Unity and 2 Monitors"
date: 2012-05-09
forum: Desktop Environments
---

### Post by Larvitz on 2012-05-09
Hi,

I have a problem with Unity running with 2 Displays.

My setup is like this: At left side, theres the Notebook (15"). Right beneath it, theres a 22" TFT Monitor (external).

The external Display should be the primary/main display. But Unity has some problem here.

- Systray icons always appear only on Notebook screen 
- Some applications (like Libreoffice) always open on Notebook screen.

Is there any way to make the external display the main display ?

Attached a screenshot. You can see, the Systray icons (like Pigdin) are only appearing on the left small display. 

It would be absolutely great if someone could help me here.

Best regards

---

### Post by Peter09 on 2012-05-09
Have you gone into the Display control panel and adjusted the look and feel? You should be able to adjust where the dash appears.

---

### Post by Larvitz on 2012-05-09
Tried that... not working.. no matter what i set there...

---

### Post by Peter09 on 2012-05-09
The netbook will not be able to show two different screens or one wide screen, you should be able to use the FN+screen key to hardware switch between netbook or screen or both(identical). Don't think the software setup is the issue here.

---

### Post by cortman on 2012-05-09
Have you tried setting it with xrandr? In a terminal-

```
xrandr --output HDMI1 --primary
```

That assumes you're using HDMI for the external monitor connection. If it's VGA, use VGA1. If DVI, use DVI1, etc.
You can also set the notebook screen to be either left or right of the primary using xrandr.

---

