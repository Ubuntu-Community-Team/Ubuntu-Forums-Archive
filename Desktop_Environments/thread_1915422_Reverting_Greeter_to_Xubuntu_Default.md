---
title: "Reverting Greeter to Xubuntu Default"
date: 2012-01-26
forum: Desktop Environments
---

### Post by iposner on 2012-01-26
Installed the latest Xubuntu. Then I (foolishly) installed some stuff from the Ubuntu desktop which replaced the Xubuntu greeter with the lightdm greeter from Ubuntu 11.10. Now I want to revert it back to the Xubuntu original, but how?

---

### Post by LewisTM on 2012-01-26
Edit your /etc/lightdm/lightdm.conf file
Change the line greeter-session to

greeter-session=lightdm-gtk-greeter

---

### Post by iposner on 2012-01-28
So I've done that and I get the blue background wallpaper (default) that's the same as the default wallpaper once you log on. However the menu of logins looks like some kind of default gnome list, with a picture of a computer at the top, not a Xubuntu logo. Have I got to fix something else?

---

### Post by LewisTM on 2012-01-30
> **iposner said:**
> So I've done that and I get the blue background wallpaper (default) that's the same as the default wallpaper once you log on. However the menu of logins looks like some kind of default gnome list, with a picture of a computer at the top, not a Xubuntu logo. Have I got to fix something else?
That's what I have too, no worries.

---

