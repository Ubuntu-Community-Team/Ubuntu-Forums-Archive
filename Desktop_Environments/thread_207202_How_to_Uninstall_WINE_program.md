---
title: "How to Uninstall WINE program"
date: 2006-07-01
forum: Desktop Environments
---

### Post by vasimakhtar on 2006-07-01
Hi
How can I uninstall programs installed through WINE?
thanks

---

### Post by digimars on 2006-07-01
Run 
```

uninstaller

```
from the command line, it will bring up a new window that you can use to uninstall programs installed through Wine.

---

### Post by vasimakhtar on 2006-07-01
Thanks. I appreciate your help.

---

### Post by digimars on 2006-07-01
Glad to help.

Some other usefull commands are winefile, it opens up an Explorer like window that lists the contents of all of your drives.

And if you need to manually remove a program, look in /home/<user>/.wine/drive_c (that's where your programs are installed).

---

### Post by Adr3nalin on 2007-09-05
I love you linux geeks!

thanks for the help guys.

i wanted to uninstall divx...u saved me.

---

### Post by santiagoward2000 on 2007-09-05
> **digimars said:**
> Some other usefull commands are winefile, it opens up an Explorer like window that lists the contents of all of your drives.

Hey! You forgot the most important of all commands! winemine :lolflag:

Anyway, aren't all these commands available through Aplications/Wine ?

---

### Post by Jammy4041 on 2007-11-29
Thankyou, I needed to unistall something, but this worked!

---

### Post by globs98 on 2007-12-14
Hi, I don't see the program that I would like to uninstall in uninstaller. Can you help me?

---

### Post by Bugsy969 on 2007-12-20
> **globs98 said:**
> Hi, I don't see the program that I would like to uninstall in uninstaller. Can you help me?

what are you trying to remove? and what version of wine are you useing?

---

### Post by (((X))) on 2007-12-28
I also recomend you to delete unneded pathlinks in /etc/ld.so.conf

/usr/lib32
/usr/X11R6/lib32
/lib32

they are no longer needed now you uninstalled WINE, this makes your Ubuntubox more secure or so..

---

### Post by lazoneleo on 2008-05-14
> **digimars said:**
> Glad to help.

Some other usefull commands are winefile, it opens up an Explorer like window that lists the contents of all of your drives.

And if you need to manually remove a program, look in /home/<user>/.wine/drive_c (that's where your programs are installed).

Hi
I still have problem of after uninstalled the CS2 on wine. restart the ubuntu then the wine still have appear the CS2 application inside? is that fully remove already. Or other method can totally remove CS2?

---

