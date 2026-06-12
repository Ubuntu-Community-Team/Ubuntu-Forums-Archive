---
title: "removing... gtk sounds in fvwm?"
date: 2009-08-16
forum: Desktop Environments
---

### Post by diehardyouth on 2009-08-16
Hi,

When I'm in FVWM I have some annoying sounds that happen when I click cancel buttons, or an urgent window will come up and other actions. I'm thinking they're from GTK but I have no idea how to get rid of them. I was wondering if anyone knew how I could get rid of them.



Thanks,

Harold

---

### Post by VCoolio on 2009-08-16
I'm experimenting to get rid of this in lxde / openbox. There are some options:

1. run gnome-settings-daemon to have the same settings as in gnome (if you disabled the sounds in system > preferences > sound they will be gone in fvwm also. Better would be to find the system config file where sound theme settings can be configured.

2. sometimes it's enough to add the line "blacklist canberra-gtk-module" to /etc/modprobe.d/blacklist.conf

3. you could also try to remove /etc/X11/Xsession.d/52-libcanberra-gtk-module_add-to-gtk-modules elsewhere. 

Let us know what works.

---

### Post by ve4cib on 2009-08-16
I had the exact same problem with Fluxbox.  The best solution I came up with was to simply purge the Ubuntu-Sounds package.  Since I disable the sounds in Gnome, and don't want them in any of my other environments it just made sense to get rid of them.

---

### Post by diehardyouth on 2009-08-17
> **VCoolio said:**
> I'm experimenting to get rid of this in lxde / openbox. There are some options:

1. run gnome-settings-daemon to have the same settings as in gnome (if you disabled the sounds in system > preferences > sound they will be gone in fvwm also. Better would be to find the system config file where sound theme settings can be configured.

2. sometimes it's enough to add the line "blacklist canberra-gtk-module" to /etc/modprobe.d/blacklist.conf

3. you could also try to remove /etc/X11/Xsession.d/52-libcanberra-gtk-module_add-to-gtk-modules elsewhere. 

Let us know what works.

1.) running gnome-settings-daemon worked (and made my windows actually look a little prettier lol, any idea why?) but long term i'm not too satisfied with running this all the time. i want to keep a lightweight setup
2.) i haven't added the line to my blacklist but i checked lsmod and it doesn't show up. thoughts?
3.) i'll try on next reboot



thanks,

harold

---

### Post by VCoolio on 2009-08-17
> **diehardyouth said:**
> 1.) running gnome-settings-daemon worked (and made my windows actually look a little prettier lol, any idea why?) but long term i'm not too satisfied with running this all the time. i want to keep a lightweight setup
gnome-settings-daemon also uses your gnome theme settings. So you can change your theme with gnome-appearance-properties if g-s-d is running.

> 2.) i haven't added the line to my blacklist but i checked lsmod and it doesn't show up. thoughts?

Maybe it only runs when it is called to do something, i.c. making these horrible sounds (is there actually anyone that appreciates them?).

---

### Post by diehardyouth on 2009-08-20
2.) didn't work
3.) worked. i:

```
sudo mv /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules.bak
```

and that was enough to make it work. 

there has to be some config somewhere though. this will work for now. thanks!

---

