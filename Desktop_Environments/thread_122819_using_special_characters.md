---
title: "using special characters"
date: 2006-01-28
forum: Desktop Environments
---

### Post by dsd on 2006-01-28
How does one go about getting special characters in Ubuntu? Occasionally I want to use special characters such as an e with an acute e', but I have no idea how to enter them. In Windows I would normally just press Alt+130.

---

### Post by ticlo on 2006-01-28
You can use CTRL + shift + [hexadecimal unicode character code] (this only works for GTK+/GNOME). So for e-acute (é, character code 00E9), you can use

CTRL + shift + E9

Leading zeroes are to be left out. 
You can look up unicode character codes in the character map, Applications->Accessories->Character Map. The character map can also be added to your panel.

---

