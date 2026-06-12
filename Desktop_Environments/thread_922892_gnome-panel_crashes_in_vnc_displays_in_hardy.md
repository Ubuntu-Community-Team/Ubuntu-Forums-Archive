---
title: "gnome-panel crashes in vnc displays in hardy"
date: 2008-09-17
forum: Desktop Environments
---

### Post by taz205 on 2008-09-17
When I launch a new gnome-session using tightvncserver and then vnc into that display, gnome-panel restarts whenever I close an application. It never happens on :0, only in other displays (:1, :2...).

My ~/.vnc/xstartup file just contains:
gnome-session &

Is there something inherent to gnome-panel (or even gnome-session) that prevents you from running multiple instances on different screens? Or do I maybe have something set incorrectly?

---

