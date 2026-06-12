---
title: "Terminal: Stop Paste from Taking Effect without Enter"
date: 2006-08-22
forum: Desktop Environments
---

### Post by jackn on 2006-08-22
When in terminal, pasting (CTRL-SHIFT-v) is carried out immediately, as if ENTER had been pressed.

I will use paste to, say, add a copied filename to a command, and as soon as the paste is carried out, the machine processes the command. This doesn't allow me to consider the command before executing it.

How can I paste and have the terminal wait for me to hit ENTER?

Jackn

---

### Post by nephish on 2006-08-22
make sure when you copy, you do not copy a newline character (line break). Then, i think it will work.

---

### Post by jackn on 2006-08-22
Thanks, Nephish. 

Didn't know. Now it's just fine.

Jackn

---

### Post by HAARP on 2006-08-22
I often copy files out of nautilus. When pasting, nautilus copies the file, whereas text apps paste the filename. The problem with that is, when copying a filename, there seems to be a newline charater with it automaticly. Pretty irritating in terminal. Is there any way to stop this?

---

