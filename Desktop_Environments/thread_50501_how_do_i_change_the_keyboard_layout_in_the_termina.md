---
title: "how do i change the keyboard layout in the terminal?"
date: 2005-07-20
forum: Desktop Environments
---

### Post by graigsmith on 2005-07-20
hi, whenever i installed i used the wrong keyboard layout.  Now i want to change it.  i'm not talking about the terminal in gnome, i'm talking about the one you get to via ctrl-alt-f1.  how do i change its keyboard layout.

---

### Post by Phixion on 2005-07-20
[QUOTE=graigsmith]hi, whenever i installed i used the wrong keyboard layout.  Now i want to change it.  i'm not talking about the terminal in gnome, i'm talking about the one you get to via ctrl-alt-f1.  how do i change its keyboard layout.[/QUOTE]

System > Preferences > Keyboard?

---

### Post by graigsmith on 2005-07-20
[QUOTE=Phixion]System > Preferences > Keyboard?[/QUOTE]
 no, that only changes the keyboard layout in gnome.  i want to change the keyboard layout in the terminal thingy, you know that one you press ctrl-alt-f1 to get to.

---

### Post by graigsmith on 2005-07-20
oh, i figured it out, you just type 
loadkeys us
in the console.

---

### Post by graigsmith on 2005-08-06
oops, after a reboot the keyboard went back to dvorak.  how can i set the keyboard to the standard us keylayout permenantly?.    loadkeys did it, but then after a reboot the dvorak layout was back.

---

### Post by Xterminator on 2005-08-07
sudo dpkg-reconfigure console-data

---

### Post by graigsmith on 2005-08-08
[QUOTE=Xterminator]sudo dpkg-reconfigure console-data[/QUOTE]
 thanks, that did the trick :)

---

