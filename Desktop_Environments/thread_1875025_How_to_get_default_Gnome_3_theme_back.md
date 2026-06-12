---
title: "How to get default Gnome 3 theme back"
date: 2011-11-04
forum: Desktop Environments
---

### Post by sameerbo on 2011-11-04
I have installed Ubuntu 11.10 and have gnome-shell on top of it.

I overwrote /user/share/gnome-shell/theme folder with some other theme, without taking backup of original theme.

how do I get original theme back. Do I have to remove gnome-shell and re-install it again?
Is there easier way to get original theme back?

Thanks
Sameer

---

### Post by nilarimogard on 2011-11-04
I guess the best way would be to reinstall GNOME Shell:
```
 sudo apt-get install --reinstall gnome-shell
```

---

### Post by sameerbo on 2011-11-04
Once I go back home I will try this

---

### Post by typhoon_tip on 2011-11-04
Yes do that command, but I suggest you to empty the directory ~/themes/Adwaita first. You don't need to re-install entire gnome shell if you just undid the themes, this command will be enough:

```
sudo apt-get install --reinstall gnome-themes-standard
```

Adwaita is included there (the default theme).

---

### Post by sameerbo on 2011-11-04
Thanks I tried re-installing just the gnome-themes-standard after emptying 'theme' folder. If doesn't get default theme back.

re-installing gnome-shell works. now I finally got my original theme.

Thanks a lot to both of... :)

---

