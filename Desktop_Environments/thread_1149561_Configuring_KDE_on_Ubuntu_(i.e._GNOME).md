---
title: "Configuring KDE on Ubuntu (i.e. GNOME)"
date: 2009-05-05
forum: Desktop Environments
---

### Post by svivian on 2009-05-05
Hopefully a simple question - is there a config app for KDE? I'm using Ubuntu which is obviously GNOME, but I've installed a few KDE apps (Kate and Amarok).

I'd like to play about with the appearance of the KDE apps, particularly setting the main fonts and sizes to match what I have under
Preferences > Appearance > Fonts.

(The ideal solution of course would be if I can set KDE apps to grab the settings from GNOME, including fonts & colors, for true consistency. But I don't change themes very often anyway.)

---

### Post by kpkeerthi on 2009-05-05
I think it is 'systemsettings' but I'm not very sure.
Press ALT+F2 and the enter **systemsettings**

---

### Post by element_G on 2009-05-05
Try qtconfig first, I think systemsettings will require a few more packages to be installed.
There should be an option under gui (widget) style named GTK+, using this will allow KDE apps to use the GTK+ theme

---

### Post by oldos2er on 2009-05-05
System, Preferences, Qt 4 settings.

---

### Post by svivian on 2009-05-06
I've tried the Qt 4 settings including setting a very small font size, but it's not changing my KDE applications, even after a restart.

---

### Post by raindog469 on 2009-06-03
Same problem here.... bring up qtconfig-qt4 and change the font, restart KDE apps and it has no effect, but bring up systemsettings and there's nowhere to change the font (Appearance just gives me Icons and Emoticons.)  Running Jaunty.

I guess I could actually log into KDE4 and try to find it there, but I get enough weird graphical artifacts in Kmail and Akregator (subject of another thread once I get a few more screenshots) that I'm afraid of what would happen if I did.

---

### Post by element_G on 2009-06-03
recently i set up Xubuntu and wanted amarok to use the GTK theme (available in systemsettings under style). I had the same trouble with systemsettings and iirc what fixes it is running amarok, quitting and then opening systemsettings. No clue why that works (if it actually does).

---

