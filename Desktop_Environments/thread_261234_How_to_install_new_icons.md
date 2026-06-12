---
title: "How to install new icons?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Monstroxus on 2006-09-20
[http://www.gnome-look.org/content/show.php?content=44539](http://www.gnome-look.org/content/show.php?content=44539)

I want to install a nice icon pack (see above link) in Ubuntu Dapper, but how to do this? Can anyone help me? Thanks!

---

### Post by X.Cyclop on 2006-09-20
Download these icons to your desktop. Then, open Theme Manager (System > Preferences > Theme), drag & drop your icons package and select them: **Theme Details** > Icons tab.

;)

---

### Post by spockrock on 2006-09-20
oops beat me to it.

---

### Post by aysiu on 2006-09-20
You don't *need* to do it for the root user, too, unless you want a consistent look, even when launching administrative applications.

By the way, the proper way to open it would be ```
gksudo gnome-theme-manager
``` Even better, though, would be to do ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
``` That way, you won't have to keep changing root's themes every time you change yours.

---

### Post by Monstroxus on 2006-09-20
You mean I have to drop the package into the screen which mentions all the different themes, like clearlooks, humanity theme etc? I thought this was for the border themes only not icons. Do I have to extract the package first before drag 'n drop?

---

### Post by X.Cyclop on 2006-09-20
> You mean I have to drop the package into the screen which mentions all the different themes, like clearlooks, humanity theme etc?
Yes, into Theme Preferences.

> Do I have to extract the package first before drag 'n drop?
No.

;)

---

