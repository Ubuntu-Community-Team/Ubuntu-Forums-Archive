---
title: "change default desktop manager"
date: 2011-10-08
forum: Desktop Environments
---

### Post by malakar.subhendu on 2011-10-08
Nautilus is the default desktop manager in gnome.
I want to change it some other file manager (like Dolphin). Please help me to change it.

---

### Post by Copper Bezel on 2011-10-08
Well, Dolphin doesn't manage the KDE desktop. There are other applications that can draw the desktop, but most of them are lighter-weight and relatively feature-poor in comparison to Nautilus. They include things like Compiz's wallpaper plugin or nitrogen, which simply render a background image (or a set of them) with no icon support at all, as well as more rudimentary file-manager-style desktops with some bonus features, like XFCE's xfdesktop.

Disabling Nautilus as the desktop manager is easy - run gconf-editor from Alt+F2 and navigate to apps/nautilus/preferences, then untick "show desktop." But you can't get KDE's Plasma desktop without using the whole package. I'm not certain how well the Plasma desktop works under Gnome - I know it's integrated with KDE's panel, for one thing.

---

### Post by malakar.subhendu on 2011-10-08
SORRY SORRY SORRY.
I wanted to change the file manager and not the desktop manager.
I wanted to use dolphin as the default file manager in place of nautilus in gnome.
I have KDE installed, but it's many applications specially the networking are not good. so i wanted to use the dolphin file manager.
also KDE does not show the gnome application properly.

---

### Post by raja.genupula on 2011-10-08
have you tried this ?

[http://www.linuxquestions.org/questions/linux-software-2/change-of-default-file-manager-700122/](http://www.linuxquestions.org/questions/linux-software-2/change-of-default-file-manager-700122/)

---

### Post by Copper Bezel on 2011-10-08
raja, that's a bit messy.

Instead, change (or add) this line in .local/share/applications/mimeapps.list, but with the appropriate .desktop for Dolphin instead. I think it's just dolphin.desktop.

```
inode/directory=nautilus.desktop;
```

---

### Post by raja.genupula on 2011-10-09
> **Copper Bezel said:**
> raja, that's a bit messy.

Instead, change (or add) this line in .local/share/applications/mimeapps.list, but with the appropriate .desktop for Dolphin instead. I think it's just dolphin.desktop.

```
inode/directory=nautilus.desktop;
```

Thanks for the suggestion .I Will remember it.

---

### Post by binary00mind on 2011-10-09
There is another way, very simple 

```
exo-preferred-applications
```
:wink:

---

### Post by Copper Bezel on 2011-10-09
exo-preferred-applications requires exo-utils. It's an Xfce thing.

---

### Post by binary00mind on 2011-10-09
> **Copper Bezel said:**
> exo-preferred-applications requires exo-utils. It's an Xfce thing.Well, you could be right. Since I always install everything, kde, xfce, gnome, enlightenment etc. 

On the other hand I have 1 fresh install of 11.04 (on Vbox) and I did not installed anything there xfce related except few kde & gnome apps and I changed default file manager to krusader. 

The exo-utils was there. So now I don't know if it comes with Gnome as a default package or not (like after fresh install) 
or it came as a dependency while I was installing these few apps from kde & gnome that I mentioned above.

Very good, pointing this out.

---

### Post by Copper Bezel on 2011-10-09
> So now I don't know if it comes with Gnome as a default package or not (like after fresh install) 
or it came as a dependency while I was installing these few apps from kde & gnome that I mentioned above.
No, it's definitely not there on a default install, but it's a dependency for Thunar and a couple of other Xfce apps that tend to get used beyond the Xfce desktop.

---

