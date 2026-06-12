---
title: "Changing the title of a window?"
date: 2006-12-05
forum: Desktop Environments
---

### Post by Hoag on 2006-12-05
Hey all.

I'm not sure if this is in the right place, so, forgive me if it's not.

I'm hoping to find a way to change the title of a window when I start the program.

I.E, a program I run in Wine has the title "C:\Directory\Program.exe". I'm looking for a way to change it to the name of the window itself, just to "Program".

I'm running gnome, on Ubuntu 6.06 LTS.

Can anyone help me, or at least let me know if it's possible?

Cheers.

---

### Post by mannheim on 2006-12-05
A program called wmctrl is one utility that can do this. It's in the repositories, so "sudo apt-get install wmctrl" or whatever, to install it. To change the name of one window whose name contains the string "Prog" to "New Name", do something like

```
wmctrl -r "Prog" -N "New Name"
```

---

### Post by Hoag on 2006-12-05
Awesome, I'll give it a try when I get home.

Thanks for the speedy response. :)

**Update**

Wmctrl has the function I'm looking for. However, is there a way I can set the rename at startup so it detects it and does it automatically? Otherwise, it forgets it as soon as I close the window, and I have to do it each time.

Cheers.

---

