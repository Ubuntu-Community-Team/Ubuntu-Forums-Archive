---
title: "Gnome theme changes for `sudo' (Solved)"
date: 2005-11-29
forum: Desktop Environments
---

### Post by xerxesdaphat on 2005-11-29
Hi. I have a very pretty Gnome theme with custom icons and all that. However, when I do something as the superuser (like `sudo nautilus', or even using synaptic or other administration tools which require me to enter the superuser password), the theme changes to this godawfully ugly default theme. Now I don't mind that much, but the problem is that the icon theme does not differentiate between files and directories, so it's very easy to think you're opening a folder but instead launch a programme. Is there anyway to set the superuser gnome theme to the same one my normal user account is?

Thankyou,

-Tom

---

### Post by Xian on 2005-11-29
[QUOTE=xerxesdaphat]Is there anyway to set the superuser gnome theme to the same one my normal user account is?[/QUOTE]
Sure, but first you'll check and make sure your theme is also located in /usr/share/themes and iconset in /usr/share/icons. Then it is just a matter of running the following command:

$ sudo gnome-theme-manager

---

### Post by xerxesdaphat on 2005-11-29
Ah!! That worked perfectly. Thankyou very much! So prompt too haha barely as soon as I'd finished posting it hehe.

Thankyou,

-Tom

---

