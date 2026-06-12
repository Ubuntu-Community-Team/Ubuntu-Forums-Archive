---
title: "Where's the Program?"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Ingla on 2005-11-21
Hi.

I just did a routine upgrade with the Upgrade Manager. It installed a program called netpbm (graphics conversion). Very nice, but it didn't create any menu item, I can't find it in /usr/bin/, and the terminal returns "no such command" on typing its name and doesn't bring it when I type part of the name and hit TAB. Of course, I don't have a clue what other command might open it.

Anyone know about where it might be and how to open it? Or is this some sort of "background" program or plugin which works in something else?

Thanks.

---

### Post by aysiu on 2005-11-21
Have you tried this? ```
locate netpbm
``` or ```
man netpbm
```

---

### Post by kperkins on 2005-11-21
netpbm is a commandline tool for converting one graphic format to another, and to manipulate images (along the lines of imagemagick).  It's acually a package of many different programs. Open up a terminal, and type in man netpbm, to learn more. 
Or check out [http://netpbm.sourceforge.net/](http://netpbm.sourceforge.net/)
The people who make [Gallery]("http://gallery.menalto.com/") recommend netpbm over imagemagick--or at least some of them think it makes better thumbnails.

---

### Post by Ingla on 2005-11-21
Both of those worked. Thanks.

---

### Post by dcstar on 2005-11-21
[QUOTE=aysiu]Have you tried this? ```
locate netpbm
``` or ```
man netpbm
```[/QUOTE]
I find "whereis xxxxx" works well with any runnable programs.......

---

