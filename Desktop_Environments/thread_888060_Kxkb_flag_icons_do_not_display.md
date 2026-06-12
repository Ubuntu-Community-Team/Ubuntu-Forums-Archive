---
title: "Kxkb flag icons do not display"
date: 2008-08-12
forum: Desktop Environments
---

### Post by vertago1 on 2008-08-12
I have enabled the Kxkb tool for keyboard layout switching. Specifically I have it setup to switch between us and ee, but the locale flag icons aren't displaying. The KDE4-"System Settings"-"Regional & Language"-"Keyboard Layout" tool is what I used to change the configuration. While the keyboard layouts work, and the Ctrl-Alt-k shortcut will toggle the layout I was hoping to get Kxkb to see the locale flags. Right now the flag images are located at:

/usr/share/locale/l10n/<Map>/flag.png

What do I need to do to get Kxkb to see this flag images when I am using kde4?

---

### Post by vertago1 on 2008-10-12
after playing around with some packages I believe the problem was fixed by:

sudo dpkg-reconfigure locales

not quite sure, but I did manage to get the problem resolved

---

