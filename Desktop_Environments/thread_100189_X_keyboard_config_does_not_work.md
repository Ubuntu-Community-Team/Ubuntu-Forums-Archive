---
title: "X keyboard config does not work"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Snifffurt on 2005-12-07
Hello

After trying to configure my Keyboard with "sudo dpkg-reconfigure xserver-xorg" several times and several different variants, I came to the conclusion that I'm not going to make it this way.

My Language is German and my Keyboard is Swiss, so it should be de_CH or so.

Here is my actual Xorg.conf, where no special chars like email AT or umlauts and any other accessed trhrouch Alt Gr. :

[http://nopaste.info/index.php?id=8117853fdc](http://nopaste.info/index.php?id=8117853fdc)

What is wrong with it? What would the right Keyboard setting be like?

Regards

Sniff

---

### Post by Snifffurt on 2006-02-26
Hello

After quite a while the user mario.rimann came up to me with a solution for this problem.

It was verry simple. In my /etc/X11/xorg.conf I had in the Keyboard section:
```
Option "XkbLayout" "ch"
Option "XkbVariant" "ch"
```
But this was wrong. The right setting is:
```
Option "XkbLayout" "ch"
Option "XkbVariant" "de"
```
Now it works at a glance. Thanks@mario.

Regards

Snifffurt

---

