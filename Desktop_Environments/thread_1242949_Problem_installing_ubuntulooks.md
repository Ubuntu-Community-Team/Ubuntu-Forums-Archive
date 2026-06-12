---
title: "Problem installing ubuntulooks"
date: 2009-08-17
forum: Desktop Environments
---

### Post by darthenstein on 2009-08-17
Hey everyone,

Ubuntu 9.04 Jaunty

Long time reader first time poster.

I am trying to install the GTK+ theme engine 'ubuntulooks' because my appearance window gives me the error "This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed".

I have downloaded the appropriate file, gtk2-engines-ubuntulooks_0.9.12-12_i386.deb.

When I try to install this with Package Installer, I get the error message, "Error: Breaks existing package 'human-theme' conflict: gtk2-engines-ubuntulooks ()"

Does anyone know what I should do here?  If it means removing human-theme, I can live without it, but I just don't know how to do that.

Thank you all very much!

---

### Post by jerrrys on 2009-08-17
first off, before posting this i went to **synaptic package manager** and did a complete removal of human themes.  sometime removing pre-installed ubuntu packages can do bad things. so before i told you its ok to remove, i did it on my system and i see no ill effects. just be sure your on a different theme when you do this.  as far as the theme "ubuntulooks", i have never tried it so your on your own from there...good luck :)

---

### Post by zerhacke on 2009-08-17
You don't need to use a .deb file and you don't need to uninstall human themes.

Use synaptics and search for ubuntulooks.  Or, if you're a terminal person, use the terminal and apt-cache search ubuntulooks.  Ubuntulooks is in the repositories so there's no need to look for it on the net, and there's no need to manually uninstall things and run the risk of uninstalling too much, as synaptics or apt-get will automatically uninstall only what is needed to go.

---

### Post by darthenstein on 2009-08-18
Hey it works great!  Thank you!

---

