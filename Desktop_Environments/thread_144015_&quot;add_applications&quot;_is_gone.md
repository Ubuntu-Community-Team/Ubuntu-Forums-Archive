---
title: "&quot;add applications&quot; is gone?"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Cirrocco on 2006-03-13
today I go to my ubuntu menu to go software shopping and I can't because "add applications" is missing from the menu.

can someone tell me what the shell command is to run that?

---

### Post by aysiu on 2006-03-13
gnome-app-install

---

### Post by bluevoodoo1 on 2006-03-13
gksudo gnome-app-install

---

### Post by aysiu on 2006-03-13
bluevoodoo's right--you need the *gksudo*.

---

### Post by Cirrocco on 2006-03-13
what's the difference between: "sudo" and "gksudo"

---

### Post by bluevoodoo1 on 2006-03-13
[QUOTE=Cirrocco]what's the difference between: "sudo" and "gksudo"[/QUOTE]

gksudo will bring up a little graphic entry box for your password, with sudo, you write your password in the terminal.

---

### Post by Cirrocco on 2006-03-13
awesome

thank you both very much

---

### Post by chrluc on 2006-03-13
mine is gone today as well but the above commands did nothing to return it it asked for a password and it was aceppted but then nothing, any ideas?could it have been an update done today?

---

### Post by ronmarley1 on 2006-03-13
If you got to System -->Administration --> Synaptic Packet Manager and search for gnome-app-install and install it, it'll be back on the Applications menu (or you can run it from the terminal, as mentioned above).

---

