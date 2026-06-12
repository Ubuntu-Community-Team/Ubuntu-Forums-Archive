---
title: "conky donest open."
date: 2009-12-26
forum: Desktop Environments
---

### Post by phillychease on 2009-12-26
this is what it says when i run it.

```
phillychease@phillychease:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.

```

---

### Post by Isengrin on 2009-12-26
Please post your ~/.conkyrc so I can test it. :3

---

### Post by phillychease on 2009-12-26
well im noob at this.
but after i put $ sudo apt-get install conky
and i run it $ conky

the thing i posted above happens.

---

### Post by Isengrin on 2009-12-26
Oh~
I guess you don't have a .conkyrc, wich is the config file for conky.

Then, let's copy the default to you home directory:
```
cp /etc/conky/conky.conf ~/.conkyrc
```

And see if it works now with a very simple and boring conky.

---

### Post by Isengrin on 2009-12-26
Either if it worked or not, you can look at here. [http://bbs.archlinux.org/viewtopic.php?id=39906](http://bbs.archlinux.org/viewtopic.php?id=39906)

There is plenty of conky example screenshots with their configs from a swarm of awesome guys and gals. :3
Just copy the config of the one you like, paste it in your text editor and save it as ~/.conkyrc

---

### Post by phillychease on 2009-12-26
> **Isengrin said:**
> Oh~
I guess you don't have a .conkyrc, wich is the config file for conky.

Then, let's copy the default to you home directory:
```
cp /etc/conky/conky.conf ~/.conkyrc
```And see if it works now with a very simple and boring conky.


cool it wooooorks! thanks! and thanks for the link too! :)

---

