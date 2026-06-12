---
title: "Xubuntu 12.04, 12.10 and 13.04 MouseCursorSize issues"
date: 2013-04-22
forum: Desktop Environments
---

### Post by superm4n on 2013-04-22
the following seems to have finally fixed the ongoing mousepointer size issues I have been having with the XFCE desktop in Xubuntu over the past year(s).

In 13.04: to set mousepointer theme to DMZ-Black and 48 size

in Settings-Manager-MouseAndTouchpad select DMZ-Black and set size to 48.

sudo update-alternatives --config x-cursor-theme
select the manual DMZ-Black option

add following lines to ~/.Xdefaults
Xcursor.theme: DMZ-Black
Xcursor.size: 48

then
chmod 555 ~/.Xdefaults
and reboot

---

### Post by slickymaster on 2013-04-22
For those who prefer, and feel more comfortable, using GUIs, they can use [B]dconf-editor.

[/B]In a terminal window:
```
sudo apt-get install dconf-tools
```
Then, under System Settings, just select dconf editor and the GUI for the dconf will open. After that, and in the left panel, just click on org -> gnome -> desktop and then select interface.
Once interface is selected, on the panel to the right, the tenth line is the one where you'll have to change the value. Just double click on the value (it should be 24, by default) and correct it to the value you desire.

---

