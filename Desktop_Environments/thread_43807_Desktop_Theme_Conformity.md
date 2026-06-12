---
title: "Desktop Theme Conformity"
date: 2005-06-23
forum: Desktop Environments
---

### Post by sinisterguy on 2005-06-23
Hey everybody,

Just recently reinstalled Ubuntu. Its made a lot of progress since I first installed the preview release. Anyway, my question was: How can I make all my apps look the same (between GTK 1.x, GTK 2.x and QT). I noticed some qt-gtk bridge thing to make gtk apps look like QT but then I can't thing of a way to change the QT theme from gnome. Also, for GTK 1.x apps, I remember that in an earlier version, I installed a theme switcher for it, and nothing happened when I switched themes. Thanks for your time,

Lukas

---

### Post by desdinova on 2005-06-23
try running from a console

switch - to change the GTK1 theme

qtconfig - to change the QT theme from within Gnome

you may need to iinstall these via Synaptic

---

### Post by sinisterguy on 2005-06-23
[QUOTE=desdinova]try running from a console

switch - to change the GTK1 theme

qtconfig - to change the QT theme from within Gnome

you may need to iinstall these via Synaptic[/QUOTE]
 Hi,

I tried what you said. For GTK 1.x , I switched to the Industrial theme, but when I opened a GTK 1.x app, it still used the ugly old theme. For QT, I don't know how to install the theme without KDE. I am also looking for the Industrial theme for QT. Thanks for your time,

Lukas

---

### Post by desdinova on 2005-06-23
what is in your $HOME/.gtkrc file?

---

### Post by sinisterguy on 2005-06-23
```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/Industrial/gtk/gtkrc"

include "/home/lukas/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

That's my /home/lukas/.gtkrc file

---

### Post by gil-galad on 2005-06-23
Make sure you have the gtk-engines-industrial theme installed.  Personally I just use the industrial theme in gnome, because that sets up both gtk1 and gtk2 engines to use it.

---

### Post by sinisterguy on 2005-06-23
i had the theme installed. and now that i've opened the file, it seems to have changed. The only thing remaining is to get my QT apps looking industrialish. any advice you can give me there? Too bad most of the good music apps on linux are QT/KDE based.

---

### Post by gil-galad on 2005-06-23
[QUOTE=sinisterguy]i had the theme installed. and now that i've opened the file, it seems to have changed. The only thing remaining is to get my QT apps looking industrialish. any advice you can give me there? Too bad most of the good music apps on linux are QT/KDE based.[/QUOTE]
 I don't even have the qt libs installed ;)

---

### Post by sinisterguy on 2005-06-24
Well, I've solved the problem. I switched to KDE. I figured it wasn't worth the headaches to stay with gnome. I've been wanting to try kubuntu for a while anyway. I'm liking more now than I ever did. Don't get me wrong, gnome is still a great desktop, but I think KDE is catching up in the world of consolidation which I've always admired in gnome.

---

