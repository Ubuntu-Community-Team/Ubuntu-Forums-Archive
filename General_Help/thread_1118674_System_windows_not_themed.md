---
title: "System windows not themed"
date: 2009-04-07
forum: General Help
---

### Post by jermsie on 2009-04-07
System windows like Synaptic Package Manager are not theming like the rest of the windows, such as Nautilus

Here is an [example screenshot]("http://dl.getdropbox.com/u/38257/Screenshot.png")

Why is this and how can it be changed?

---

### Post by kpkeerthi on 2009-04-07
[http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

---

### Post by jermsie on 2009-04-07
> **kpkeerthi said:**
> [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

Thank you :)

Here is the solution, as seen in the link:

```
To fix this, run these three commands in a terminal. 
They will cause your own theme, font, and icon preferences 
to always be used by the root user.

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

---

