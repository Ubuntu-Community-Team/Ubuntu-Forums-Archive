---
title: "How do you change the Grub boot screen?"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Dakaru on 2006-06-20
Ok I recentley installed XFCE and the log off screen changed to the Xubuntu one, and I like this one alot more.

So my question is how do I change the start up one to be the same? So they are matching and such ;).

---

### Post by Dakaru on 2006-06-20
[QUOTE=Dakaru]Ok I recentley installed XFCE and the log off screen changed to the Xubuntu one, and I like this one alot more.

So my question is how do I change the start up one to be the same? So they are matching and such ;).[/QUOTE]
Bump..

---

### Post by aysiu on 2006-06-20
[This](http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6) may help.

---

### Post by Dakaru on 2006-06-21
[QUOTE=aysiu][This](http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6) may help.[/QUOTE]


Not making much sense to me..

---

### Post by aysiu on 2006-06-21
Sorry. I just realized that gives the wrong command. It should be this: ```
sudo update-alternatives --config usplash-artwork.so
``` Paste that into the terminal. The rest should be self-explanatory.

---

### Post by Dakaru on 2006-06-21
That did it. The Xubuntu one rocks.

Thanks again.

---

