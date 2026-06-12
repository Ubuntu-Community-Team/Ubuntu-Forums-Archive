---
title: "How can I kill the desktop and then start it up again?"
date: 2011-11-05
forum: Desktop Environments
---

### Post by Closrapexa on 2011-11-05
When I used Ubuntu, I used to disable gdm loading at startup, and then used /etc/init.d/gdm stop or start to kill the desktop or start it up again. How can I do the same thing in XFCE? I mean the "master process" used to start or stop the desktop?

---

### Post by gsmanners on 2011-11-06
I believe the proper usage is:

```
sudo service gdm stop
```

And in 11.10:

```
sudo service lightdm stop
```

---

### Post by Closrapexa on 2011-11-06
Cool, it worked, thanks! On a related note, what process do I disable if I want to boot to the console? xfdesktop?

---

