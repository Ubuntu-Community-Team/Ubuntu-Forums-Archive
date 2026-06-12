---
title: "keep apt-get going after closing the window?"
date: 2009-01-04
forum: General Help
---

### Post by Tactical Fart on 2009-01-04
First off, while I'm not new to linux, I'm still inexperienced so I may be ignorant to some things.
Second, I like the command line. Don't know why.

Anyway, here's my situation. I have the G1 phone, and installed an ssh client called Connectbot. It works just fine, and I have the server running okay. I can even run apt-get and install stuff at will. But I've noticed that when I close the program on my phone (or close the terminal on the machine itself) the "install" (Is it technically installing while it's still fetching files?), the process stops. Is there a way to make it proceed regardless?

---

### Post by Ahadiel on 2009-01-04
```
sudo apt-get install screen
```
then
```
screen *command*
```
check the manual page for more information.

---

### Post by Tactical Fart on 2009-01-04
Thanks for the help. Screen seems to be a bit tricky, but I think I've got it down good enough.

---

