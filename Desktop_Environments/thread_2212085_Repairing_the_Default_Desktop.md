---
title: "Repairing the Default Desktop"
date: 2014-03-19
forum: Desktop Environments
---

### Post by Asymtotic on 2014-03-19
I was in the process of adding Gnome Tweak to my system and my computer locked up (first time ever in Linux, BTW).  Now when I log in using Unity 3d, I have no docking bar.  I can't use Gnome either.  I can only log in using the Unity 2d mode.  Anyone have idea how to get this straightened out?  I have used computers for a fairly long time. I'm very comfortable with command line.

Any help would be appreciated!

---

### Post by grahammechanical on 2014-03-19
It depends upon the version of Ubuntu that you are using. I am assuming that it is 12.04. Unity 2D uses Metacity as the window compositor. Unity 3D uses Compiz as the window compositor. So, there is something wrong with Compiz and Unity. But things change over time and it is a long time since I used 12.04 so this advice may be incorrect.

To reset Launcher icons

```
unity --reset-icons
```

To reset Compiz

```
dconf rest -f /org/compiz/
```

That command may not work because 12.04 may not have dconf-tools installed.

```
sudo apt-get install dconf-tools
```

This may or may not work

```
 setsid unity
```

That is all that I can offer.

Regards.

---

### Post by olliemonster on 2014-05-14
If that doesn't work you could go into a tty console with ctrl alt f1 and reinstall compiz and unity from there ```
sudo apt-get purge compiz unity
``` ```
sudo apt-get install compiz ubuntu-desktop
``` however that should be a last resort really i'd just recomend upgrading to 14.04 since its been released now.

---

