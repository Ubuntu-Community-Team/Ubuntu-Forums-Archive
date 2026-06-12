---
title: "How can I reinstall gnome files from kubuntu?"
date: 2010-11-07
forum: Desktop Environments
---

### Post by tridentblack on 2010-11-07
I set up Kubuntu today because the keyboard input was messed up in GNOME, due to some file being corrupted. Does anybody know how to replace GNOME files in Kubuntu? I'm new to it, trying to find my way around.

Thanks!

---

### Post by sikander3786 on 2010-11-07
> Does anybody know how to replace GNOME files in Kubuntu? I'm new to it, trying to find my way around.

Hi. Which files do you want to replace? Can't quite understand that statement...

---

### Post by tridentblack on 2010-11-07
> **sikander3786 said:**
> Hi. Which files do you want to replace? Can't quite understand that statement...

Hi. All I know is that my keyboard stopped working in GNOME, but not kubuntu (KDE) or at the login screen. I am assuming some GNOME file became corrupt, because it used to work just fine and works in KDE. So I am trying to find a way to replace gnome files with non-corrupt versions.

---

### Post by sikander3786 on 2010-11-08
> **tridentblack said:**
> Hi. All I know is that my keyboard stopped working in GNOME, but not kubuntu (KDE) or at the login screen. I am assuming some GNOME file became corrupt, because it used to work just fine and works in KDE. So I am trying to find a way to replace gnome files with non-corrupt versions.
```
sudo apt-get install --reinstall ubuntu-desktop
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

should do that.

---

