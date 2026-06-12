---
title: "is it possible"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Choness on 2006-06-27
is it possible to have upgraded to dapper 6.06 and still have xfce and your settings?

---

### Post by PriceChild on 2006-06-27
Erm yes...

A normal upgrade will keep all your old settings, but will take errors with it too.

Pricey

---

### Post by Choness on 2006-06-27
ok and do you know the command to check and make sure you have it? in terminal

---

### Post by PriceChild on 2006-06-27
well you should just be able to run:

```
sudo update-manager
```

It will inform you there is a new version - Dapper and ask whether you want to upgrade.

Ensure that you have backed up ALL important information just incase, i'm not taking responsibility :P

---

### Post by Choness on 2006-06-27
lol ok thanks a bunch

---

### Post by bruce89 on 2006-06-27
[QUOTE=PriceChild]well you should just be able to run:

```
sudo update-manager
```
[/QUOTE]
aysiu recommends ([http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)) using gksudo for graphical apps.  So run ```
gksudo update-manager
``` or just go to System>Administration>Update Manager.

---

### Post by aysiu on 2006-06-27
[QUOTE=bruce89]aysiu recommends ([http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)) using gksudo for graphical apps.  So run ```
gksudo update-manager
``` or just go to System>Administration>Update Manager.[/QUOTE]
If you wonder why I recommend it, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by bruce89 on 2006-06-27
[QUOTE=aysiu]If you wonder why I recommend it, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[/QUOTE]
Oy, I just added that to my post!

---

### Post by Choness on 2006-06-27
what is the command in terminal to see what version of of ubuntu you have

---

### Post by aysiu on 2006-06-27
```
cat /etc/issue
``` I think.

---

