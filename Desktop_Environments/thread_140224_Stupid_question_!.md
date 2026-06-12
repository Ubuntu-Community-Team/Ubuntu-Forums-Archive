---
title: "Stupid question !"
date: 2006-03-05
forum: Desktop Environments
---

### Post by stonex on 2006-03-05
How can I enter like an admin ? I need to set up modem driver , but I don't know how to run root terminal as Admin .Help please !

---

### Post by Xian on 2006-03-05
Read the [RootSudo](https://wiki.ubuntu.com/RootSudo) section in the wiki.

---

### Post by OffHand on 2006-03-05
or type: 

sudo passwd root

then type your normal password
after that enter root password twice

Goodluck

---

### Post by aysiu on 2006-03-05
For commands, type *sudo* in front.

For example, if your command is *./install.sh*, use *sudo ./install.sh* instead, and it'll execute the shell script with root privileges.

If you want a graphical browser, press Alt-F2 and type ```
gksudo nautilus
```

---

### Post by stonex on 2006-03-05
Thanks ! I will try now !

---

