---
title: "Custom application launcher woes"
date: 2024-06-09
forum: Desktop Environments
---

### Post by currentshaft on 2024-06-09
asd as

---

### Post by &amp;KyT$0P# on 2024-06-09
> **currentshaft said:**
> when I launch it, it opens two windows: Terminal, which is opening another window for st.

This defeats the point of what I'm trying to do.

The [FONT=monospace]Terminal=true[/FONT] line is explicitly requesting this behavior.  Does the launcher not work if you instead set [FONT=monospace]Terminal=false[/FONT] or entirely remove the [FONT=monospace]Terminal=[/FONT] line?

---

### Post by vanadium on 2024-06-10
That means the desktop cannot make an association between the launcher and a running window. To fix that, add a "StartupWMClass=&#8230;" line to indicate the WMClass of such terminal window.

---

### Post by Holger_Gehrke on 2024-06-10
> **currentshaft said:**
>  ... why do I even have to ask such a basic question in 2024?

This is partially on the developers of st for not including a .desktop file - but then none of the suckless tools do, the developers [believe in using a really minimal environment]("https://suckless.org/philosophy/") instead of the big DEs that are prevalent today; their programs don't even have any way to set options other than editing a header file before compiling. So the other part of the blame goes to you, for using a program that's not really meant for Ubuntu - the suckless tools are meant to be their own environment that's more minimalistic than than any flavour of Ubuntu.

Holger

---

### Post by currentshaft on 2024-06-12
d 1 2

---

### Post by Holger_Gehrke on 2024-06-12
> **currentshaft said:**
> Why hasn't Gnome implemented a simple launcher/dock app creator to help befuddled users like me? Surely I'm not alone ...

They have. It's called 'alacarte'. Since I use Xubuntu I don't know whether it's part of the Ubuntu default install, but it is in the repositories.

Holger

---

### Post by Dennis N on 2024-06-12
> Is there any way to avoid having 2+ icons appears for st?

I've seen that with a few applications. No guarantees, but try adding the following line to the st.desktop file:
StartupWMClass=st

> Why hasn't Gnome implemented a simple launcher/dock app creator?
There is a utility to make .desktop files called Desktop Files Creator (not made by the Gnome Project). See screenshot.

---

### Post by currentshaft on 2024-06-13
> **Dennis N said:**
> I've seen that with a few applications. No guarantees, but try adding the following line to the st.desktop file:
StartupWMClass=st


Unfortunately does not work and I still get multiple dock tiles, nor does the icon I have set (Icon=xterm).

---

### Post by &amp;KyT$0P# on 2024-06-13
Try this? -
```
[Desktop Entry]
Type=Application
Name=st
Icon=xterm
Exec=/usr/local/bin/st
StartupNotify=true
StartupWMClass=st-256color
```

---

### Post by currentshaft on 2024-06-13
Thank you, halogen! That works great, I just had to adjust:

Icon=utilities-terminal

Great suggestions all around.

---

