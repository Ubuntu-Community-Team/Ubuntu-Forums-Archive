---
title: "Change Ubuntu 12.04 login screen to kubuntu login screen?"
date: 2012-06-29
forum: Desktop Environments
---

### Post by Kimizor on 2012-06-29
Greetings programs!
I installed Ubuntu 12.04 with wubi (yes, I know, I belong in "absolute beginner talk") and hated unity. I deleted unity, gnome, and unity 2D but I still get the ubuntu login screen with the wallpaper I had in unity. Is there any way to change this? I've tried configuring kdm but that didn't fix it... 
Thanks,
Kimi

---

### Post by msammels on 2012-07-03
If you have kdm installed, then you can do the following:

Open Terminal and type this:

```
sudo nano /etc/X11/default-display-manager
```

Once that file is open simply replace "lightdm" with "kdm", then restart your machine. Or you can restart X with:

```
CTRL+ALT+BACKSPACE
```

It's your choice.

---

