---
title: "Login screen looks old after applying emerald theme"
date: 2010-07-06
forum: Desktop Environments
---

### Post by Mr_VeRiTy on 2010-07-06
Hi, I tried applying an emerald theme yesterday, and when I did, it somehow affected the login screen, now it looks old and crappy like win98. I tried disabling emerald and even uninstalling it, but the login screen remains crappy, how do I get it back to the way it was?

I'm using lucid lynx with Gnome.

---

### Post by sisco311 on 2010-07-06
Try to cange its theme. Add gnome-appearance-properties to GDM's autostarted applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. 

Select a new theme/wallpaper/font. 

Log in and remove gnome-appearance-properties from GDM's autostarted applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Mr_VeRiTy on 2010-07-06
> **sisco311 said:**
> Try to cange its theme. Add gnome-appearance-properties to GDM's autostarted applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. 

Select a new theme/wallpaper/font. 

Log in and remove gnome-appearance-properties to GDM's autostarted applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
That fixed it thanks :)

---

### Post by JoerBrando on 2011-04-09
Worked for me as well! :)

Thank you! :popcorn:

---

### Post by sisco311 on 2011-04-10
> **JoerBrando said:**
> Worked for me as well! :)

Thank you! :popcorn:

My pleasure.

Welcome to the forums!

---

### Post by JoerBrando on 2011-04-17
Hello and thanks for the warm welcome, :)

I have a new problem now.
Every time i start my computer and comes to the login windows,
the "Theme chooser" is present, and it comes back as soon as i restart my computer.

Any ideas?

Edit: My bad, guess i just hadent removed the autostart function. :)

---

