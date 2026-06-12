---
title: "help me find file"
date: 2006-01-29
forum: Desktop Environments
---

### Post by gammagoat on 2006-01-29
I am trying to set up my mouse buttons with this guide HOWTO: enable a 5 Button Mouse  found in the Ubuntu wiki. My problem is that I cannot find this file to edit (/etc/X11/xorg.conf). I have looked for this by using find files and folders, using every option listed. Is there another way? Or am I just missing something?

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=gammagoat]I am trying to set up my mouse buttons with this guide HOWTO: enable a 5 Button Mouse  found in the Ubuntu wiki. My problem is that I cannot find this file to edit (/etc/X11/xorg.conf). I have looked for this by using find files and folders, using every option listed. Is there another way? Or am I just missing something?[/QUOTE]
make sure you don't mistype. X in X11 should be upper case for example (as it is in your post). what's the exact command you type to edit xorg.conf (type command in terminal, press enter. if it fails, copy and paste the command here)

---

### Post by gammagoat on 2006-01-29
This is the command and result.

sudo gedit /etc/X11/xorg.conf
Password:
sudo: gedit: command not found

---

### Post by aysiu on 2006-01-29
Notice how it says *command not found* and not *file not found*?
Gedit is the text editor in Gnome (Ubuntu).
KWrite is the text editor in KDE (Kubuntu).

You're using Kubuntu, so no Gedit.

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=aysiu]Notice how it says *command not found* and not *file not found*?
Gedit is the text editor in Gnome (Ubuntu).
KWrite is the text editor in KDE (Kubuntu).

You're using Kubuntu, so no Gedit.[/QUOTE]
yes, my bad, I keep forgetting to look where the post is located (in Kubuntu!)... use ```
sudo kwrite /etc/X11/xorg.conf
```

---

### Post by gammagoat on 2006-01-30
Thanks. I see the error in my ways.:oops:

---

