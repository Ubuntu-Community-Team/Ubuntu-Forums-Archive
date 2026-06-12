---
title: "Geany doesn't get focus"
date: 2023-07-22
forum: Desktop Environments
---

### Post by biagiopas on 2023-07-22
Ubuntu22.04 desktop with LUKS, GNOME 42.9

Geany is an advanced text editor/IDE very useful for me,
I set Geany as the default application to open text files

from the file explorer GUI
if i click on a .txt file then Geany doesn't get focus,
instead an alert/dialog is displayed which disappears after a few seconds,
this alert/dialog contains the geany logo and the file name,
to be able to assign focus to Geany I have to switch between running programs with ALT+TAB
tks in advance for help

---

### Post by ajgreeny on 2023-07-22
This sounds like a window-manager setting that is incorrect.

I do not use gnome so no longer know which **wm** gnome uses but have a look there as a start.

---

### Post by biagiopas on 2023-07-23
ajgreeny, thanks for your reply
ubuntu22.04 GNOME 42.9
FileManager: Nautilus (alias Files) 42.6

I checked what happens with other editors
with Gedit and Libreoffice the problem doesn't occur, it only occurs with Geany
more specifically, with Gedit and Libreoffice if you double-click on the file all works
however, the problem still occurs if you open the context menu with the keyboard menu key > open file >

Dconf Editor search the Nautilus configurations
also search in geany configurations in file ~/.config/geany/geany.conf
but i didn't solve the problem

I ll report directly in geany issues
[https://github.com/geany/geany/issues](https://github.com/geany/geany/issues)

---

