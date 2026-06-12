---
title: "WoP"
date: 2007-08-02
forum: Gaming &amp; Leisure
---

### Post by burt_57 on 2007-08-02
Would some one tell me how I can get rid 
of that game on my hard drive.
I don't like it and I can not find  an uninstall!
Darn it all .
I know where the file are.... but I ca not del. them  :-k

---

### Post by linksolo74 on 2008-02-01
in the World of Padman folder there is a uninstall file.

---

### Post by puppe on 2008-03-12
unfortunately it is not working but instead gives me this message
```
Could not find a usable uninstall program. Aborting.
```
when giving the commando
```
sudo sh uninstall
```
in the /usr/local/games/WoP directory  :confused:

---

### Post by Perfect Storm on 2008-03-12
```
cd
rm .WoPadman
cd /usr/local/games
sudo rm -rf WoP
cd /usr/local/bin
sudo rm -rf wop
cd
```

Should completly remove WoP (manually).

---

### Post by puppe on 2008-03-12
thanks. That was certainly fast and effective.

Still have a WoP button hanging around in my Applications menu though..?

---

### Post by Perfect Storm on 2008-03-12
```
alacarte
```

Find it, remove it ;)

---

### Post by puppe on 2008-03-12
aouch, now I feel stupid (actually looked for a way to delete a shortcut directly in alacarte but strangely enough didn't find it then...)

Solved it by doing a locate wop and ended up deleting it from
/usr/share/gnome/apps$

Will have it a bit more easy next time :)

---

