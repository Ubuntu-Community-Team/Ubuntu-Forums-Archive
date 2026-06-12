---
title: "Ubuntu save"
date: 2005-12-22
forum: General Help
---

### Post by rensu on 2005-12-22
Can someone answer me the simple question: Why my Ubuntu isnt saving my hostname. I have my hostname atm like ip60 but i want to change it to localhost. I changed it and logged of and it worked but after i restarted my computer it putted again the default hostname: ip60.

---

### Post by darth_vector on 2005-12-22
how did you change it? the best way to change it is to open the file /etc/hostname as root and replace the existing name with the new one. something like

sudo gedit /etc/hostname

should let you do that.

---

### Post by rensu on 2005-12-22
Thnx:)

---

