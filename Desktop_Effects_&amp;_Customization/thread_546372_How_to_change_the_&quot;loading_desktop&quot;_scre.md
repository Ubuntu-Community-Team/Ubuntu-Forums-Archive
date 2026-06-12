---
title: "How to change the &quot;loading desktop&quot; screen?"
date: 2007-09-08
forum: Desktop Effects &amp; Customization
---

### Post by mindtrick on 2007-09-08
How do we change Gnome's small rectangular screen which is displayed right after user password login? There was no section for it at art.gnome site.

---

### Post by chuckyp on 2007-09-08
Its called a splash screen on gnome art page.  There are gnome splashes on gnome-look also.

---

### Post by mindtrick on 2007-09-08
Thank you. But how I do apply those splash screens?

---

### Post by rainwalker on 2007-09-08
Copy the image to "/usr/share/pixmaps/splash"
```
sudo cp /location/of/image /usr/share/pixmaps/splash
```
That's where all of the splash images are. If you go there in the file browser, there's a symbolic link called "ubuntu-splash.png"
Right-click on it and choose "Properties". In that window, click the icon of the splash screen and change it to the one you want.

---

### Post by FuturePilot on 2007-09-08
You can also 
```
sudo apt-get install gnome-splashscreen-manager
```
Then System>Preferences>Splash Screen and just install you image.

---

