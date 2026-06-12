---
title: "Xfce over VNC instead of Gnome"
date: 2005-09-19
forum: Desktop Environments
---

### Post by dickohead on 2005-09-19
Good Morning,

I have just installed Xfce on two machines, both working fine. Previously when I was running Gnome on my server I could run vncviewer and see my Gnome Desktop, i have now logged in with Xfce, set it as the default and installed vncserver - yet when i run vncviewer 0.0.0.0:1 (for example) it does not load the xfce desktop, rather it loads gnome - despite xfce currently running on the server.

I have added:
```

startxfce4 &

```
 to my .vnc/xstartup file yet there is no change.

Has anyone successfully exported their xfce desktop over VNC with gnome installed? I would still like to have Gnome installed untill I become accustomed to Xfce, and if i remove Gnome will my gnome-based programs also dissapear?

---

