---
title: "Screen resolution change - GUI fails to function"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by frbe0101 on 2007-11-03
I changed the screen resolution to display for a projector, I changed the resolution back but now the GUI seems to fail to boot properly and I'm stuck with the terminal, how do I fix this?

Using a Dell Inspiron 1420 with Gusty/7.10

---

### Post by frbe0101 on 2007-11-03
Never mind fixed it my self:

1. "sudo dpkg-reconfigure xserver-xorg"
2. just let it choose the setting
3. "sudo /etc/init.d/gdm restart"
4. GUI comes up, wiped beads of sweat off, worry replaced with satisfaction.

---

