---
title: "howto unistall a dpkg installed file"
date: 2006-02-01
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-01
i did this to install gimpshop

ex. sudo dpkg -i gimpshop.deb

now u read the other post i cant save as an .xpm format any more so im takin the easy way out as i can not locate forums for gimpshop and i just want to unistall it and reinstall gimp if needs be

---

### Post by geekphreak on 2006-02-01
dpkg -r package

for more info 

man dpkg

---

### Post by ESPOiG on 2006-02-01
how can i find out were all the package files were installed :D

---

### Post by mcduck on 2006-02-01
'sudo apt-get remove name', like 'sudo apt-get remove gimpshop'. It should also be listed in Synaptic, and you can remove it there too.

---

### Post by geekphreak on 2006-02-01
Just give it the package name, for instance to uninstall gaim, type dpkg -r gaim

---

### Post by ESPOiG on 2006-02-01
the package name didnt work but the apt-get command did.... thanx it shuld be fine now

---

### Post by ESPOiG on 2006-02-01
maybe not it culdnt find the package so now i dunno wat to do again

---

### Post by ESPOiG on 2006-02-01
can neone tell me how to get rid of gimp shop or is there another program that i can use apt-get to get to make the format .xpm

---

