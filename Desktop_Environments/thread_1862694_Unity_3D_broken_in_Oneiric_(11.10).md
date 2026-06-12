---
title: "Unity 3D broken in Oneiric (11.10)"
date: 2011-10-17
forum: Desktop Environments
---

### Post by zombiezparadize on 2011-10-17
Hi,

I updated from Maveric to Natty to Oneiric today. I was still getting used to Unity when I deleted the .themes/nautilus/nautilus.rc file by mistake. When I restarted the laptop later, I logged onto Gnome-shell by default. I wasn't sure what happened so I logged out to choose to login to Unity. Now I don't even see the options "Ubuntu" or "Ubuntu 2D" in the list of sessions at the login splash.

I followed the directions on [this]("http://askubuntu.com/questions/63921/unity-3d-doesnt-work-anymore-just-shows-a-menu-on-the-top") post and got the Unity 3D interface to work again. However, I still don't see it at the login screen and I login by default to gnome-shell. Also, changing any settings at ccsm causes the whole desktop to freeze (the windows lose their title bars). 

When I run the "unity --reset" command or run "ccsm" from command line, I see the following error: 

```
/home/k/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"
```

Now I don't know if the issues are related but I thought it could be useful information. I found other copies of nautilus.rc on my system but they seem to be different for each theme. How should I create another nautilus.rc for the above folder? More importantly, how do I fix the issue with Unity. Can anyone please help?

---

### Post by zombiezparadize on 2011-10-17
bump

---

