---
title: "Border between Window Bar and App flickers in Compiz w/ Wobbly Windows"
date: 2010-05-11
forum: Desktop Environments
---

### Post by vaiocomputer on 2010-05-11
There are these little white flickers between the border between the window bar (w/ the window buttons) and the application every time I move the window.  How do you get rid of it?

---

### Post by vaiocomputer on 2010-05-12
Bump.

---

### Post by infamous-online on 2010-05-13
> **vaiocomputer said:**
> Bump.

Take a screencap so I can get a better idea as to what you mean if you don't mind.

---

### Post by vaiocomputer on 2010-05-13
These flickers or thin broken moving lines of white or black between the border of the titlebar/window bar and app only last for a brief fraction of a second once I stop moving the windows.  It happens when the shape of the windows is distorted by Wobbly Windows.  I doubt I can take a screenshot of the desktop fast enough to include them.

And I've never actually taken a screenshot before.

---

### Post by vaiocomputer on 2010-05-14
This doesn't happen with Emerald, but with GTK Window Decorator.

---

### Post by soliac on 2010-06-11
Here is a screenshot. The white bits are actually the background showing through.

---

### Post by confused_user on 2010-06-12
i get that as well, sorry no idea how tofix it but your not alone

---

### Post by eggdeng on 2010-06-12
This is because the new themes have merged the window title bar with the application menu bar by painting both the same (charcoal) colour. Using Emerald alone won't solve this because you'll still get a dark or light coloured strip under the title bar.
The solution is to use a theme which doesn't merge the two bars. The classic human themes are available from the repos. Do
```
sudo apt-get install human-theme
```
Go to System -> Preferences -> Appearance and customise as you will.

---

