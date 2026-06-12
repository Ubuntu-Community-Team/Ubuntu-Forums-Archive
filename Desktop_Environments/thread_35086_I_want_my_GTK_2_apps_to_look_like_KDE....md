---
title: "I want my GTK 2 apps to look like KDE..."
date: 2005-05-17
forum: Desktop Environments
---

### Post by z-vet on 2005-05-17
This is my first post here, so hello community.  :) 
I want my GTK 2 apps to have a same look like entire KDE (i use Plastik theme). Installed GTK2-QT-engine but it doesn´t changed nothing, it still a same ugly GTK look. Anyone can help me to solve it, please?

---

### Post by BAshworth on 2005-05-17
I too had a problem with this on Suse 9.2.  Firefox and Thunderbird were unuseable due to the font size.

I ended up switching to a Gnome based distro to fix it.

However, I do remember there being some way to install the gnome theme panel, and then you have to add in the daemon for the gnome theme engine into your kde startup.

---

### Post by SGC on 2005-05-17
Try the following:

Go to: control center > apearances and themes > GTK styles and fontes  

From there select:
- Use my KDE style in GTK applications
- Use my KDE fonts in GTK applications

---

### Post by z-vet on 2005-05-17
H-m-m...i´m stupid. I tried to look at Synaptic that runs under root and have no style applied. Thanks!

---

### Post by bored2k on 2005-05-17
Try GTK-QT theme engine: [http://www.gnomelook.org/content/show.php?content=9714](http://www.gnomelook.org/content/show.php?content=9714)

---

### Post by vanaedium on 2005-05-17
You can download by synaptic switch2, a command line theme switch with preview

---

### Post by philipacamaniac on 2005-05-17
Also, try running the KDE Control Center as root (kdesu kcontrol) to set the style/windeco/fonts/GTK-themes for applications that open with root.

---

### Post by z-vet on 2005-05-18
[QUOTE=philipacamaniac]Also, try running the KDE Control Center as root (kdesu kcontrol) to set the style/windeco/fonts/GTK-themes for applications that open with root.[/QUOTE]
 philipacamaniac, thanks for the tip. Now i have the same look for user and root apps. Thank you.

---

