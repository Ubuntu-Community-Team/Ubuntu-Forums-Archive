---
title: "Tried Xubuntu - How to Get Back the Ubuntu GDM Login Page?"
date: 2007-03-19
forum: Desktop Environments
---

### Post by dc. on 2007-03-19
Hi,

I installed xubuntu-desktop to try xfce out, but removed it some time later and returned to gnome.

Now I still have the "Xubuntu"-Boot-Splash-Screen.
However, I want to get rid of it
1) It does not have a hibernate option which I use all the time, only shutdown, restart and login
2) It doesn't look as nice ;)


Any help would be appreciated!

---

### Post by flossgeek on 2007-03-19
```
sudo update-alternatives --configure usplash-artwork.so
```

Choose usplash-default.so for the brown Ubuntu splash.

Then, run 

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

I think this is right I have encountered this problem myself too(but cannot remember off the top of my head). If the above does nothing for you, let me know and I'll look into it in more detail for you.

---

### Post by RedSquirrel on 2007-03-19
> **dc. said:**
> Hi,

I installed xubuntu-desktop to try xfce out, but removed it some time later and returned to gnome.

Now I still have the "Xubuntu"-Boot-Splash-Screen.
However, I want to get rid of it
1) It does not have a hibernate option which I use all the time, only shutdown, restart and login
2) It doesn't look as nice ;)


Any help would be appreciated!


The boot splash screen and gdm login window are two different things. ;)

For the gdm login window, you can just change the theme: there is an entry in one of the menus called  "**Login Window**" or something. I'm in Fluxbox, so I can't recall exactly where it is or what it's called, but it's in there somewhere.

---

### Post by dc. on 2007-03-21
Login Window did it!
Thanks!

---

