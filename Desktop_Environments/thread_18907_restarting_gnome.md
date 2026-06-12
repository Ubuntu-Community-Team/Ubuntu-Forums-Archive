---
title: "restarting gnome"
date: 2005-03-09
forum: Desktop Environments
---

### Post by eraos on 2005-03-09
Sometimes, when I've restarted Gnome (using ctrl, alt, backspace), it never loads up again.  I just get the console (I think it's called).  I'm asked for my user name and password and everything, so I'm obviously still in Ubuntu, but I just don't have the GUI.

How, from the console, do I load gnome?

---

### Post by krusbjorn on 2005-03-09
this happens to me sometimes too.

most of the time, "startx" works. but sometimes it says something about fonts being used by another application, or something like that. i dont know how to solve that so all i can do is "sudo reboot".

---

### Post by Stefan Sager on 2005-03-09
[QUOTE=eraos]Sometimes, when I've restarted Gnome (using ctrl, alt, backspace), it never loads up again.  I just get the console (I think it's called).  I'm asked for my user name and password and everything, so I'm obviously still in Ubuntu, but I just don't have the GUI.

How, from the console, do I load gnome?[/QUOTE]
 Start GDM, gnome display manager:
sudo gdm

---

### Post by bored2k on 2005-03-09
[QUOTE=krusbjorn]this happens to me sometimes too.

most of the time, "startx" works. but sometimes it says something about fonts being used by another application, or something like that. i dont know how to solve that so all i can do is "sudo reboot".[/QUOTE]
 Yup, after I ctrl alt backspace a couple of times It won't do it again. Startx works tho

---

### Post by eraos on 2005-03-09
Okay, thanks.  Next time it happens, I'll do that.

---

### Post by p!=f on 2005-03-09
```

sudo /etc/init.d/gdm restart

```
or if you use wajig
```

wajig restart gdm

```
should do the trick.

---

### Post by bored2k on 2005-03-09
[QUOTE=p!=f]```

sudo /etc/init.d/gdm restart

```
or if you use wajig
```

wajig restart gdm

```
should do the trick.[/QUOTE]
 Isn't startx a little bit ... easier ^o) ?


Anyway, that works too [if you can remember it] :P

BTW, wajig is not installed by default so unless you install it , it will not work.

---

### Post by rosslaird on 2005-03-09
gdm does seem to be a little wonky. On my nvidia setup, about half the time when I kot-key out of X, I don't get gdm OR a console prompt. I get the dreaded black-screen-with-little-white-dot-in-upper-left-corner. Nothing gets me out of that: not ctl-alt-bksp, not even ctl-alt-f1 for another console. I have to power off. Ouch!

On the other hand, I hardly ever have to hot-key out of X. And usually it's my own fault -- I've been monkeying around with xcompmgr or something.

---

### Post by p!=f on 2005-03-09
[QUOTE=bored2k]Isn't startx a little bit ... easier ^o) ?
[/QUOTE]
Yes, sure... but as I can read in the first post
[QUOTE=eraos]
Sometimes, when I've restarted Gnome (using ctrl, alt, backspace), it never loads up again.
[/quote]
GDM may still keep :0 display opened but actually displaying pure blank so I doubt startx will work. I just added another possibility how to get GUI back.
[QUOTE=bored2k]
Anyway, that works too [if you can remember it] :P
[/QUOTE]
startx -- :1 is my preferred way but thanks for reminder. :P
[QUOTE=bored2k]
BTW, wajig is not installed by default so unless you install it , it will not work.[/QUOTE]
Guess why I wrote "if you use". ;)

---

