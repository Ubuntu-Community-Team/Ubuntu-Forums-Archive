---
title: "how to take a screenshot in xfce?"
date: 2005-01-23
forum: Desktop Environments
---

### Post by akurashy on 2005-01-23
how to take it ? i cant find the command and i want to show it to my friend =/

---

### Post by ilari on 2005-01-23
[QUOTE=akurashy]how to take it ? i cant find the command and i want to show it to my friend =/[/QUOTE]
 If you have Gnome (and gnome-panel) installed, there should be 'gnome-panel-screenshot'.

---

### Post by akurashy on 2005-01-23
i have it but i dont have the screenshot button O_o

---

### Post by ilari on 2005-01-23
[QUOTE=akurashy]i have it but i dont have the screenshot button O_o[/QUOTE]
 If you type 'gnome-panel-screenshot' in terminal, it should open a dialog that has a 'Save' button for taking the screenshot...

---

### Post by Moobert on 2005-01-23
you can also intall imagemagick, and use the 'import' command from the console;

import -pause 5 <name of file>.<jpg or png>

it has loads of other features too, 'man import' for details.

---

### Post by jensyt on 2005-01-24
The way I did it:

sudo apt-get install scrot

Then on the commandline either just "scrot" or "scrot -s -b" to select a window and show its border in the screenshot. Works fine for me.

---

