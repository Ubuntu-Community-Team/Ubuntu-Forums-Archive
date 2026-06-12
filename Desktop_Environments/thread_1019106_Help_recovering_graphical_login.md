---
title: "Help recovering graphical login"
date: 2008-12-22
forum: Desktop Environments
---

### Post by aalinovi on 2008-12-22
Some time ago, I set things up so that I always started in terminal mode and would have to type startx to launch a window manager.

I now want to go back to how ubuntu defaulted when I first set it up but for the life of me I can't remember how I did it.

For what it's worth, I've used sysv-rc-conf and checked off GDM in every run level but no good.

Any help would be appreciated.

Thanks

---

### Post by taurus on 2008-12-22
Maybe

```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by albinootje on 2008-12-22
> **aalinovi said:**
> Some time ago, I set things up so that I always started in terminal mode and would have to type startx to launch a window manager.

I now want to go back to how ubuntu defaulted when I first set it up but for the life of me I can't remember how I did it.

For what it's worth, I've used sysv-rc-conf and checked off GDM in every run level but no good.
What happens when you do 
```

sudo /etc/init.d/gdm restart

```

---

### Post by aalinovi on 2008-12-23
Thanks to both of you.

sudo /etc/init.d/gdm start got me to where I was able to login graphically.

Then, System - Administration - Services - and check off "graphical login manager"

Thanks again

---

