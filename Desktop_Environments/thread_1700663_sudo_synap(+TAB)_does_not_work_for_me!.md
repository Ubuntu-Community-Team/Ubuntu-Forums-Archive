---
title: "sudo synap(+TAB) does not work for me!"
date: 2011-03-05
forum: Desktop Environments
---

### Post by smss on 2011-03-05
Hello.
 I have already when I typing in terminal:
 sudo synap (+ TAB)
 Was completely written.
 But now all my words like this should end I typing.
 The problem began when I had to install the program: wine
(Using the command:sudo apt-get install wine)
 But after all the steps to install ,I met with the license which was written:
 ""Press Ok to accept the License""
 "Ok" But did not in any way and I closed the terminal!
 I'm Thanks if you help me to solve this problem.
Best regards...
***smss***

---

### Post by oldos2er on 2011-03-05
Run ```
sudo dpkg --configure -a
``` When the license agreement comes up, use Tab to highlight OK then press Enter.

If I am misunderstanding your problem, please let me know.

---

### Post by smss on 2011-03-12
> **oldos2er said:**
> Run ```
sudo dpkg --configure -a
``` When the license agreement comes up, use Tab to highlight OK then press Enter.

If I am misunderstanding your problem, please let me know.
Thanks you for reply to this problem.But did not fix it by this command;```
sudo dpkg --configure -a
```;);););)

---

