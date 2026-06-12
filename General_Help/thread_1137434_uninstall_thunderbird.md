---
title: "uninstall thunderbird"
date: 2009-04-25
forum: General Help
---

### Post by wubiubiubi on 2009-04-25
Hi, I was looking to try mozilla thunderbird but decided i don't like it. i need to uninstall it now. I'm using ubuntu 9.04, and i installed it in the terminal using "sudo apt-get mozilla-thunderbird". I don't know how to uninstall it. i searched mozilla in the filebrowser, and found a text file labeled "uninstall" but it was blank and there was no option to run it. help please!

---

### Post by collinp on 2009-04-25
To remove thunderbird, run:
```
sudo apt-get remove mozilla-thunderbird
```**NOTE:**This command works for any program you have installed from apt-get or .deb files by replacing thunderbird with whatever you need to uninstall.

---

### Post by wubiubiubi on 2009-04-25
Never mind i got it to work. sudo apt-get remove didn't work, all i had to do was go into add/remove programs and uncheck it...which is wierd, considering i thought apt-get did that exact same thing, just in the terminal. thanks anyway

---

