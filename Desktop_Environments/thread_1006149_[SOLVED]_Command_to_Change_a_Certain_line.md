---
title: "[SOLVED] Command to Change a Certain line"
date: 2008-12-09
forum: Desktop Environments
---

### Post by Benismyhorse on 2008-12-09
Hi all,
Trying to make a script (Part of one) that will change the the grub boot menu timeout to 0, is there a command I can put into a script that can edit this. This file is /boot/grub/menu/lst
Thanks

---

### Post by cdtech on 2008-12-09
I corrected myself below. lol

---

### Post by cdtech on 2008-12-09
Use the "sed" command:
```
sed "s/^timeout.*$/timeout 0/" "/boot/grub/menu.lst.bak"
```
This will search the "menu.lst" for the text "timeout" along with the entire line and replace it with the new line "timeout 0".

I used a backup menu.lst (menu.lst.bak) to test it so the code above reflects my file.

Hope this helps ya........

---

### Post by Benismyhorse on 2008-12-09
Thanks the above coding worked but to get it to save I had to go:
sed -i "s/^timeout.*$/timeout 0/" "/boot/grub/menu.lst.bak"

---

