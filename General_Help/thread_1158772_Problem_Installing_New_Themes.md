---
title: "Problem Installing New Themes"
date: 2009-05-14
forum: General Help
---

### Post by bolter40k on 2009-05-14
I downloaded a new theme because i got sick of the black brown orange theme ubuntu comes with. I went to System>Preferences>Appearance.  Clicked on install theme navigated to it and it says cannot move directory over directory.  I had tried installing this theme before but to no success as it required something called kore to be installed.  If there is anyone who could help me install this theme id greatly appreciate it

---

### Post by ad_267 on 2009-05-14
You usually get that error when the theme is already installed, or there is a theme with the same name.

An alternative way to install the theme is to extract the contents of the archive and copy the theme directory into ~/.themes. You will have to turn on "show hidden files" to be able to see this directory in the file browser, or you can type in the address.

---

### Post by bolter40k on 2009-05-14
ok the theme was correctly installed now i get the theme wil not look as intended the required GTK+ theme 'kore' is not installed

---

### Post by ad_267 on 2009-05-14
Themes can be different types. Metacity themes change your Window border and GTK themes change the appearance of different controls like scroll bars. You can also get icon themes. Emerald themes are another type of window border theme that you can find out about if you want to.

Some themes come as packages that might contain a Metacity theme and a GTK theme.
So were you expecting this theme to change the controls as well as the window border? And does the window border change when you select the theme?

If you want the gtk theme too but don't have it you can install it from [http://www.gnome-look.org/content/show.php/Kore-Gnome?content=55747](http://www.gnome-look.org/content/show.php/Kore-Gnome?content=55747) (That's the Kore GTK theme).

---

### Post by Tipped OuT on 2009-05-14
> **bolter40k said:**
> ok the theme was correctly installed now i get the theme wil not look as intended the required GTK+ theme 'kore' is not installed

Usually when it says that, it's something that is needed for the theme to have it look the way it was intended. For example, another theme might say you're missing "AeroCons", which is an icon set that is intended to be used with the theme. So I would download "AeroCons" and install the icon theme, and the error would be fixed. Understand? Just figure out what "kore" is. Google.

---

### Post by extremizt on 2009-05-29
Though gnome-look and deviantart are really good with regard to number of themes available, it is a bit difficult for starters to find out good themes from these sites and install it. 

Zgegblog guys have build some amazing looking themes and they also have a Launchpad Repo. So that you could directly install themes from Synaptic Package Manager. Take a look
[http://ubuntumanual.org/posts/177/eyecandy-themes-for-ubuntu-download-via-launchpad-ppa-repo-and-be-safe](http://ubuntumanual.org/posts/177/eyecandy-themes-for-ubuntu-download-via-launchpad-ppa-repo-and-be-safe)

---

