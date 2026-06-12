---
title: "Getting Back to GDM"
date: 2008-05-08
forum: Desktop Environments
---

### Post by iflanery on 2008-05-08
A few minutes ago I decided to reinstall ubuntu-desktop (I currently have kubuntu installed). However, when I restarted my machine, I saw something a bit annoying: the loading screen still bore the Kubuntu logo and color scheme, and it took me to the  KDM.

My question: How would I be able to get back to using the Ubuntu loading screen and the GDM?

In addition, I find that the GNOME Artwork Manager no longer loads; or rather, it appears to, but disappears for a split second.

Thanks in advance.

---

### Post by aysiu on 2008-05-08
Maybe these [terminal](http://www.psychocats.net/ubuntu/terminal) commands might help? ```
sudo update-alternatives --config usplash-artwork.so
``````
sudo dpkg-reconfigure gdm
```

---

### Post by iflanery on 2008-05-08
Should I do this from inside KDE, or is it alright to do it while logged into GNOME?

Thanks. :)

---

### Post by aysiu on 2008-05-08
I don't think it matters, but if you want to be safe, I'd log out and press Control-Alt-F1, log in, type both commands, and then type ```
sudo /etc/init.d/gdm restart
```

---

### Post by iflanery on 2008-05-08
Thanks. This has been solved by using startupmanager to resolve the usplash and dpkg-reconfigure to resolve GDM. The latter seems to be kind of a quick and dirty solution, but it worked, so it's all good, I suppose.

**EDIT:** GNOME Artwork Manager still hiccups when loading. Damn.

---

