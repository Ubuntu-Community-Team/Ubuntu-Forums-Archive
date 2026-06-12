---
title: "Getting gnome to start up by default"
date: 2006-06-28
forum: Desktop Environments
---

### Post by vbeav99 on 2006-06-28
After using Ubuntu (with gnome) for about a week I decided to try out KDE and installed it...for now, I think I'm gonna stick with gnome, but the problem is that the computer now loads kubuntu as default (I can log into a gnome session though).
Is there any way to change to back to start up as gnome by default (sorry I'm really new to this stuff)

Thanks

---

### Post by Ramses de Norre on 2006-06-28
```
echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-manager
sudo rm -f /etc/rc2.d/S??kdm
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm
```

---

### Post by vbeav99 on 2006-06-28
I still see the Kubuntu logo during startup but after that it worked perfectly.

Thanks for the fast reply!

---

### Post by Ramses de Norre on 2006-06-28
That can be solved easily too ;)
```
sudo update-alternatives --config usplash-artwork.so
``` and choose the right option.

---

### Post by vbeav99 on 2006-06-28
nice, thanks again

---

