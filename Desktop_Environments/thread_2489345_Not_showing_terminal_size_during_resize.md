---
title: "Not showing terminal size during resize"
date: 2023-07-26
forum: Desktop Environments
---

### Post by jimav on 2023-07-26
**How to make gnome-terminal show the size (rows/columns) during resizing?**

This used to work.    I just installed 23.04, and am using the default desktop environment (AFAIK gnome on Wayland).

Loss of this feature will make me go back to xfce because I work on projects which use a coding standard requiring max 80-column lines, and so it is essential to be able to easily set terminals to be exactly 80 columns to easily see over-long lines when using vim.

(The only reason I came back to gnome was that xfce does not support HiDPI displays very well and, reportedly, the latest ubuntu + gnome does)

---

### Post by Xian on 2023-07-26
This behavior has been exhibited on Wayland environments. 

You could install another term such as QTerminal.
It will display the rows/columns during resizing under Wayland.

---

### Post by Holger_Gehrke on 2023-07-27
Why are you playing around with a fragile solution (setting the terminal to a specific width) instead of setting a maximum line length in vi ? While vi isn't my editor of choice, I'm quite certain that it can do that (':help textwidth' in vi should give you the relevant part of the documentation if you have the vi documentation installed).

Holger

---

