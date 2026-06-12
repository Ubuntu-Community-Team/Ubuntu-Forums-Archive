---
title: "need help with cp command"
date: 2009-03-04
forum: General Help
---

### Post by newbuntus on 2009-03-04
I entered the following command in the terminal: 

cp `ls /usr/share/pixmaps | grep .*xpm` ~/TEST2

and got this error for each matching file:

cp: cannot stat `aisleriot.xpm': No such file or directory
cp: cannot stat `baobab.xpm': No such file or directory
cp: cannot stat `blackjack.xpm': No such file or directory

what have I done wrong?

cheers

---

### Post by adult swim on 2009-03-04
try using
sudo cp /usr/share/pixmaps/*.xpm ~/TEST2

---

### Post by newbuntus on 2009-03-04
thanks that works, however I would still like to know what was wrong with the way i did it because i still dont quite understand how the backticks work. I tried all the stuff between the ticks just by itself which worked, and from my understanding the output of that should have been used in the copy command?

---

### Post by kevdog on 2009-03-04
Sounds to me like the full path is not included in the output.

---

### Post by newbuntus on 2009-03-04
Ah no wonder!

---

