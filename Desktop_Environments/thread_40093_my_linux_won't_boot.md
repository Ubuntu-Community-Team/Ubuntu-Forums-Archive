---
title: "my linux won't boot"
date: 2005-06-07
forum: Desktop Environments
---

### Post by mucovisidose on 2005-06-07
hi guys, i have some serious problem with my computer
when i boot i get to the grub screen. from there i can choose to run linux but when i do so the screen goes stays black and nothing happens (as far as i can tell)
can some one tell i there is something i can do about it? i'm a total newbie looking for help, please...

---

### Post by xao on 2005-06-07
i hate to say this, but have you tried reinstalling?

---

### Post by mucovisidose on 2005-06-08
of course it s the obvious solution but i was looking for a way which would preserve my files
any idea?

---

### Post by Takis on 2005-06-08
> i was looking for a way which would preserve my files 
Get the live cd, backup your files onto a USB stick or something, and then reinstall. When you reinstall, create a separate partition for /home.

---

### Post by xao on 2005-06-08
..and the install cd has a recover mode. it may have some tools you are looking for, though admitedly i have not messed with it.

---

### Post by mucovisidose on 2005-06-08
thx for your answers guys im going to check what i can do with your tips

---

### Post by alastair on 2005-06-08
Difficult to say. Has it ever worked? If so, what changed?

Try editing the GRUB kernel line at boot e.g.

ESC to stop at GRUB
"e" to edit a kernel boot line
select kernel line - and "e" to edit
go to the end of the line - add "vga=791" (assuming nothing like this present)
"b" to boot

Any difference?

---

