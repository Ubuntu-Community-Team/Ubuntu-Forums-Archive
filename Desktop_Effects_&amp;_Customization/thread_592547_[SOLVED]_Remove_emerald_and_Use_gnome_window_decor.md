---
title: "[SOLVED] Remove emerald and Use gnome window decoration with Compiz"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by jlinho on 2007-10-26
Hello everybody,

My compiz on Gutsy(just upgraded from Feisty)  uses Emerald for window borders. 
I want to use the gnome-metacity window borders with compiz in Gutsy (like I did it with compiz-fusion on feisty).
How can I use it (gnome/metacity borders with compiz)  instead of Emerald ?

Thanks in advance for your help !

---

### Post by Steve1961 on 2007-10-26
Try this command:

gtk-window-decorator --replace &

---

### Post by Chade on 2007-10-26
> Try this command:

gtk-window-decorator --replace &
Thanks, that did it for me as well!

---

### Post by Forlong on 2007-10-26
> **jlinho said:**
> How can I use it (gnome/metacity borders with compiz)  instead of Emerald ?
You said it yourself in the title:
```
sudo apt-get remove emerald
```

---

### Post by jlinho on 2007-10-26
> Try this command:

gtk-window-decorator --replace &

=> Thanks ...

> sudo apt-get remove emerald
=> but I can have emerald installed and not enabled by default ...

Thanks

---

### Post by jlinho on 2007-10-26
Oh... I am experiencing some minor visual bugs with gtk-window-decorator :
The upper window border is sometimes not paint entirely

---

### Post by SniperSlap on 2008-03-21
Worked for me!  Thanks...

GTK is much more practical for window borders.

---

