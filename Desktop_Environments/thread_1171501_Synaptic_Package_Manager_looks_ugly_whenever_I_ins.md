---
title: "Synaptic Package Manager looks ugly whenever I install a new GTK 2 Theme."
date: 2009-05-27
forum: Desktop Environments
---

### Post by Missing_Number on 2009-05-27
For some reason, whenever I install a GTK 2 theme (in this case, Human-Reprise at [http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045](http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045) ), certain aspects of the system like GDebi Package Installer, Computer Janitor, and Synaptic Pacakge Manager look ugly.  The loading bar is an ugly solid blue, even though it's not supposed to be, and the grey interface of the system looks like something out of Windows 95 and not anything like the theme I installed.  I installed the theme and the necessary icon-set properly.

What am I doing wrong?  Can somebody check the link and make sure I didn't screw something up or forget to do something?  How is a theme properly installed?

---

### Post by mcduck on 2009-05-27
Your not doing anything wrong, the thing here is that you are most likely installing those themes into your personal theme directory, while those administrator programs run as different user (root) who doesn't have the same themes.

You *could *install the themes system-wide, into /usr/share/themes, but there's also another (in my opinion nicer ) way to fix this, just link your own theme directory into root's, and root will always have the same themes available you have:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by KOld Iron on 2009-05-27
Or you could just leave it ugly on purpose. That's the reason, I have never changed the themes or icons for root. Everytime I see the (admittely) ugly interface I know I work with root privileges and I need to be more careful than usual.

---

