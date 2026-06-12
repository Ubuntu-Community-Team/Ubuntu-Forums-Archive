---
title: "GTK ugly when running sudo"
date: 2006-07-22
forum: Desktop Environments
---

### Post by mucha on 2006-07-22
When I run a gtk-application with sudo the gtk is really ugly. How do I make the sudo-applications to use the same gtk-theme as I normally use?

---

### Post by aysiu on 2006-07-22
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by ardchoille on 2006-07-22
> **aysiu said:**
> ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

Very nice little trick that :)

---

### Post by aysiu on 2006-07-22
The other option is ```
gksudo gnome-theme-manager
``` and selecting the root theme by hand.

---

### Post by ardchoille on 2006-07-22
> **aysiu said:**
> The other option is ```
gksudo gnome-theme-manager
``` and selecting the root theme by hand.

That is what I have been using.. but I like your advice better because I don't have to keep changing the theme in gksudo gnome-theme-manager :)

---

### Post by saracen on 2006-08-03
I didn't have this problem before (with a fresh dapper install).  But now after the latest updates I do.  Any idea why?

---

### Post by 3rdalbum on 2006-08-03
Any idea why I've never had this problem on either of my computers?

---

