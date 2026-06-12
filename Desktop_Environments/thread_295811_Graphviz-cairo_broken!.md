---
title: "Graphviz-cairo broken!"
date: 2006-11-08
forum: Desktop Environments
---

### Post by bmhm on 2006-11-08
[FONT="Verdana"]Hi,

the package "graphviz-cairo" is broken. I can't reinstall or remove it, since it tries to run a "graphviz-cairo.postinst" after any action, which is broken "Line 9: unknown command: dot".

Line 9 contains:
dot -c
;;

I can't install ANYTHING... HELP!!! :confused: :( [-o< [/FONT]

---

### Post by bmhm on 2006-11-09
Some1 please? urgent, I am unable to do ANYTHING! :((

---

### Post by bmhm on 2006-11-09
[FONT="Verdana"]Sorry for getting impatient *up*

But noone's online in your IRC-Channel :([/FONT]

---

### Post by christhemonkey on 2006-11-09
As a quick dirty workaround;
You could open the "graphviz-cairo.postinst" and comment out the dot -c line.

```
gksu gedit graphviz-cairo.postinst 
```

And then change line 9 to:
```
# dot -c 
```

---

### Post by bmhm on 2006-11-09
Tried. Didn't work :(

Btw: Package is red in Synaptic.

Ty for your answer anyway.

---

### Post by christhemonkey on 2006-11-09
Does it still give the same error message?

Sorry if this is rude, but did you save the file after commenting out line 9?

---

### Post by bmhm on 2006-11-09
It's ok, you may check everything.

Yes I DID save, still get error/return code 127.
i did use vi
inserted #
:wq
 as root of cause

---

### Post by deresh on 2006-11-21
quick and dirty hack that works!

$ sudo ln -s /usr/bin/test /usr/bin/dot
$ sudo apt-get -f install
$ sudo rm -f /usr/bin/dot

---

### Post by rune_kg on 2006-11-22
> **deresh said:**
> quick and dirty hack that works!

$ sudo ln -s /usr/bin/test /usr/bin/dot
$ sudo apt-get -f install
$ sudo rm -f /usr/bin/dot

YES! Worked perfectly for me. I can now apt-get stuff without errors.

TXH!

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by lydic on 2006-11-23
Make sure you install the graphviz package

---

