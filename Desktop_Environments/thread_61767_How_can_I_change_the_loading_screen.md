---
title: "How can I change the loading screen?"
date: 2005-09-02
forum: Desktop Environments
---

### Post by Ibuntu_52 on 2005-09-02
I want to change the little bar after the login screen that shows all the applets loading.

Does anyone know how I can do this?

I would like to change it to a very simple loading bar.

---

### Post by Crimguy on 2005-09-02
[QUOTE=Ibuntu_52]I want to change the little bar after the login screen that shows all the applets loading.

Does anyone know how I can do this?

I would like to change it to a very simple loading bar.[/QUOTE]
 How do I change the GNOME splash screen?

To change the splash screen, put the downloaded image in an unobtrusive location (since it will need to remain there as long as you want it to be the splash screen). A logical location would be ~/.gnome/splash.png (or .jpeg if the image is a JPEG). Then, edit the GConf key /apps/gnome-session/options/splash_screen using the Configuration Editor (Panel menu->System Tools->Configuration Editor) or the commandline tool gconftool-2.

[http://art.gnome.org/faq.php#q8](http://art.gnome.org/faq.php#q8)

---

### Post by Ibuntu_52 on 2005-09-02
Heh, I thought that only refered to the image after that, lollin.

thanks   :-)

---

