---
title: "remove everything from grub"
date: 2009-05-26
forum: General Help
---

### Post by kuipou on 2009-05-26
i installed ubuntu on a sd card and everytime i boot the sd card the tons of option that are displayed before loading how can i remove them completely? so that when i boot the sd card ubuntu load without this menu before

---

### Post by jocko on 2009-05-27
To hide the boot menu:
```
gksudo gedit /boot/grub/menu.lst
```Find this section:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#[/COLOR]hiddenmenu
```Remove the [COLOR=Red]#[/COLOR]:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```You'll still be able to see the menu if you press Esc just before the menu would normally appear.

---

### Post by kuipou on 2009-05-27
strange? the file is empty

---

### Post by taurus on 2009-05-27
Try the /boot/grub/menu.**[COLOR="Blue"]lst[/COLOR]**.

```
gksudo gedit /boot/grub/menu.lst
```

---

