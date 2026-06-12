---
title: "Cairo-dock Launchers indicators don't work"
date: 2011-01-27
forum: Desktop Environments
---

### Post by Grizzil on 2011-01-27
cairo 2.2.0-4(no-OpenGL) 
ubuntu AMD64 10.10 
gnome + compiz

Launchers indicators only work when I check the "Mix launchers and applications" box under behaviour/taskbar menu option. I already set the class of the launchers with the "grab" button in the "modify launcher menu", any suggestions ? I'm lost:(

---

### Post by Bobhuber on 2011-01-28
> **Grizzil said:**
> cairo 2.2.0-4(no-OpenGL) 
ubuntu AMD64 10.10 
gnome + compiz

Launchers indicators only work when I check the "Mix launchers and applications" box under behaviour/taskbar menu option. I already set the class of the launchers with the "grab" button in the "modify launcher menu", any suggestions ? I'm lost:(
Are you talking about the captions (name of the launcher?)

---

### Post by Grizzil on 2011-01-28
Hi & tanks for the reply.
No I'm talking about the indicator (the small triangle or ball of light under the application launcher) that tell you your application is running.

---

### Post by Bobhuber on 2011-01-29
> **Grizzil said:**
> cairo 2.2.0-4(no-OpenGL) 
ubuntu AMD64 10.10 
gnome + compiz

Launchers indicators only work when I check the "Mix launchers and applications" box under behaviour/taskbar menu option. I already set the class of the launchers with the "grab" button in the "modify launcher menu", any suggestions ? I'm lost:(
OK to be honest I never noticed the indicators because they did not show at all for me.
Heres what I did. Open config,appearance,indicators.There are 3 items to check.

Indicator of active window - Draw indicator above the icon (checkmark)
indicator of active launcher - Display an indicator on application icons too (checkmark)
                                        Draw indicator above the icon (checkmark)
For some reason I had to disable,apply and recheck these items then  reapply them for it to work.Hope this helps.

You also need to play with the dock view (3D Plane,Curve etc.) and the selection under indicators to link the indicator to its icon. This will effect the whether or not the indicator is on the top or bottom of the icon and your ability to see it.

---

### Post by Grizzil on 2011-01-29
Hi & tanks for your time
but it doesn't work for me, I have now choose another configuration that suit my desktop use.
Tank you for your help

---

