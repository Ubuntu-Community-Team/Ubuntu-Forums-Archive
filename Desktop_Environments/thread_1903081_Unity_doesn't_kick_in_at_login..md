---
title: "Unity doesn't kick in at login."
date: 2012-01-01
forum: Desktop Environments
---

### Post by christovic on 2012-01-01
I start up my 11.10 installation, and login to the unity environment, but the unity environment doesn't load; instead I get my 'File Edit View Go' ect. and from thereon I can't do anything. No unity sidebar, or applets on the top bar appear, and from thereon, I need to load up terminal through my bookmarks, and then use the command

```
unity &> /dev/null & disown
```

to start unity. 

Can anyone help?

---

### Post by grahammechanical on 2012-01-01
The log in screen is controlled by something called LightDM, then it hands over control of the desktop to the Compiz compositing or window manager. 

Have you disabled the Unity Plugin in Compiz Configuration Settings Manager? Have you tried to set some of the compiz effects? Some of them cause a conflict with Unity. Try to revert the changes you have made. You may need to login to Ubuntu 2D to do this.

Regards.

---

