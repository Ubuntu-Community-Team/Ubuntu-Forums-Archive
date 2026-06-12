---
title: "help with editing my xorg.conf in terminal"
date: 2005-04-11
forum: Desktop Environments
---

### Post by JimmyJazz on 2005-04-11
hey I changed a line in my xorg.conf and it broke xorg now I'm stuck with just a terminal screen and I'm having trouble editing my xorg.conf from the terminal (nano) anyways can anyone help me, I just need to edit one line and things will be back to normal.  These terminal text editors are tricky.

---

### Post by mendicant on 2005-04-11
Open the file up using nano:

% nano /etc/X11/xorg.conf
Use the arrow keys to move around in the file.
Type new stuff and/or backspace over what you don't want.
Hit Ctrl-X to exit.
  It will ask you if you want to save, and you can just hit Y
  It will ask you what file to write to, and you can just press Enter.

Then restart gdm:
% /etc/init.d/gdm restart

---

### Post by JimmyJazz on 2005-04-11
ok ha I just figured out I was typing ect and not etc, I feel pretty dumb now.

---

