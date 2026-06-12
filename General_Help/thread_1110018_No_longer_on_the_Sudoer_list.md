---
title: "No longer on the Sudoer list"
date: 2009-03-29
forum: General Help
---

### Post by MathIsDelicious on 2009-03-29
I went to install something earlier, and I noticed that add/remove application wasn't in the menu, and I looked into a bit deeper, and apparently, I'm not on the sudoer list, and I can't su either. When I try to ctrl+alt+f1 a black screen appears and some text at the top flashes stuff. 

I don't know when it appeared or why. This is the only account on the machine.

---

### Post by nebileix on 2009-03-29
Restart and start recovery mode follow by running command shell or line. Can't really remember.

Run the following command.
> & visudo
Add the following line to the bottom of the sudo list.

"your name" ALL=(ALL) ALL

You should be able to sudo after that.

---

