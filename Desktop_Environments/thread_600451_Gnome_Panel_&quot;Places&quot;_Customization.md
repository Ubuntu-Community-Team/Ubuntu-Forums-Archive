---
title: "Gnome Panel &quot;Places&quot; Customization"
date: 2007-11-02
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-11-02
Does anyone know if there's a way to remove entries like "CD/DVD Creator" amongst others from the Places menu in Gnome panel? I'm using Fedora but I trust the procedure will be the same since it's a Gnome issue.

---

### Post by zerwas on 2007-11-06
Hello,

It works. But you have to edit the source code.

[list=1]
[*]Open a terminal.
[*]```
mkdir -p .p/gnome-panel && cd .p/gnome-panel
```
[*]```
sudo apt-get install build-essential
```
[*]```
sudo apt-get build-dep gnome-panel
```
[*]```
apt-get source gnome-panel
```
[*]```
cd gnome-panel*
```
[*]gedit gnome-panel/panel-menu-items.c
[list=1][*]Go to line 609.
[*]Now delete for example this, to remove "CD/DVD-Ersteller" entry:
```
	panel_menu_items_append_from_desktop (places_menu,
					      "nautilus-cd-burner.desktop",
					      NULL);
```
[*]You can also define your own entries like this.[/list]
[*]Now compiling:
```
./configure --prefix=/usr
make
sudo make install ### Oder: sudo checkinstall
```
[*]That's it. log in again or do:
```
killall gnome-panel
```
[/list]

Good night,
zerwas

---

### Post by ShareBuntu on 2007-11-07
Wow, thanks for the response! You seem like you know what you're doing there. Unfortunately I'm trying to do this on Fedora 7. You don't happen to know the RPM equivalent commands to apt-get, do you? I'd rather follow the advice of an expert than seriously mess things up so close to the F8 upgrade! :)

---

### Post by zerwas on 2007-11-08
You should ask in the Fedora forums about this. :-) They should be able to help you out. Perhaps you can also give them the information i gave you.

---

### Post by conehead77 on 2007-11-09
Very nice, worked excellent for me!

Danke :)

---

