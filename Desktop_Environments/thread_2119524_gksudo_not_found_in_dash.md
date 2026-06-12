---
title: "gksudo not found in dash"
date: 2013-02-24
forum: Desktop Environments
---

### Post by johnny28 on 2013-02-24
:mad: When I write gksudo or gksu in the dash, are not found and therefore no more I can add, for example, gksudo nautilus!

---

### Post by sudodus on 2013-02-24
Welcome to the Ubuntu Forums :-)

I suggest that you use the hotkey combination

***ctrl + alt + t***

to get a terminal window, and then write the command line. There is command completion, so if you write ```
gks
``` and press TAB once it will complete to the first fork
```
gksu
``` without a space afterwards. That means that there are other alternatives. Press TAB once more, and the alternatives are printed
```
gksu             gksudo           gksu-properties  

```
so if you type **d** and TAB again it will complete to

```
gksudo
``` with a space afterwards. Now it has found a unique instance.

---

### Post by Frogs Hair on 2013-02-24
Dash has command prompt as well, which is Alt + F2.

---

### Post by zombifier25 on 2013-02-24
> **Frogs Hair said:**
> Dash has command prompt as well, which Ctrl + Alt + F2.

I think you meant Alt + F2, unless you're referring to tty2...

If you want to type an exact command (gksu nautilus), press Alt + F2. It has a log of all commands typed, which is handy.

---

### Post by matt_symes on 2013-02-24
Hi

gksudo is just a symbolic link to gksu. Do you have this on your machine ?
```

matthew-S206:/var/lib/dpkg % ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 Dec 28 14:25 /usr/bin/gksudo -> gksu*
matthew-S206:/var/lib/dpkg % 

```

Kind regards

---

### Post by Frogs Hair on 2013-02-24
> **zombifier25 said:**
> I think you meant Alt + F2, unless you're referring to tty2...

If you want to type an exact command (gksu nautilus), press Alt + F2. It has a log of all commands typed, which is handy.

Thanks for the correction. ;)

---

### Post by grahammechanical on 2013-02-25
The Dash finds applications. You are asking it to find a command. Try searching the Dash for Terminal. You will get a choice of three. You can use the standard terminal to run the command

```
gksudo nautilus
```

Regards.

---

