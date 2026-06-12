---
title: "Khotkeys"
date: 2005-04-18
forum: Desktop Environments
---

### Post by !nkubus on 2005-04-18
anyboy experiencing khotkeys errors or trouble, i'm not able to start the program i have the following error when i try to start it with the console, if i try through kcontrol it won't start either:

```

ERROR: Communication problem with khotkeys, it probably crashed.

```

i want to use konqueror as my main browser but without mouse gesture it's a no-go for me  :???:

---

### Post by !nkubus on 2005-04-20
it seems i'm the only one with this error :S tat' s bad :(

---

### Post by jago25_98 on 2005-06-28
Known bug but it's not in the Ubuntu bugzilla.

same here:

j@ETHEL:~$ khotkeys
ERROR: Communication problem with khotkeys, it probably crashed.
j@ETHEL:~$  

j@ETHEL:~$ ls -l  /usr/bin/khotkeys
-rwxr-xr-x  1 root root 2900 2005-04-06 03:44 /usr/bin/khotkeys
j@ETHEL:~$ 

j@ETHEL:~$ khotkeys -v
Qt: 3.3.3
KDE: 3.4.0
KHotKeys: 2.1
j@ETHEL:~$  

Can't actually find the proper khotkeys homepage either:
[http://www.google.com/search?hl=en&lr=UTF-8&oe=UTF-8&q=site%3Akde.org+khotkeys](http://www.google.com/search?hl=en&lr=UTF-8&oe=UTF-8&q=site%3Akde.org+khotkeys)
[http://datschge.gmxhome.de/khotkeys.html](http://datschge.gmxhome.de/khotkeys.html)

---

### Post by TwoSouls on 2005-11-25
[QUOTE=!nkubus]it seems i'm the only one with this error :S tat' s bad :([/QUOTE]

Hi there,

I am having the same problem... 

$ twosouls@linux:~> khotkeys -v
$ Qt: 3.3.5
$ KDE: 3.5 (RC1) Level "a"
$ KHotKeys: 2.1

TwoSouls

---

### Post by onni on 2005-12-23
Same problem here.

---

### Post by fdoving on 2006-05-11
[http://bugs.kde.org/show_bug.cgi?id=119438](http://bugs.kde.org/show_bug.cgi?id=119438)

It shouldn't be started that way.

---

### Post by blueball on 2006-06-15
Same problem here, 
but I can access khotkeys via kcontrol -> regional -> khotkeys.

---

### Post by yaztromo on 2006-08-24
Same problem here. KDE 3.5.4

---

