---
title: "Boot Without X"
date: 2005-07-13
forum: Desktop Environments
---

### Post by douceur on 2005-07-13
Is there a way to make Ubuntu boot without loading X?  I'm playing around with misc server things right now (apache, proftpd, etc), and I'd rather just boot to terminal, log in, and then startx if I really need it.  Any help would be appreciated.  Thanks.

---

### Post by Xian on 2005-07-13
This should work:
```
$ sudo update-rc.d -f gdm remove
```
Or if you prefer...

Use the first command to disable GDM and get a console prompt instead.
Use the second command to enable GDM again.

This way you can basically just toggle it on and off.

```
$ sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
```
$ sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```

---

### Post by wylfing on 2005-07-13
If the purpose of those last two commands wasn't clear enough: the first one will turn OFF the automatic loading of X, and the second one will turn X back ON. Although almost any renaming will do the trick, I like to rename init scripts to things like "disabled.S13gdm" so that I am very, very aware of what I have done. It's like writing clear comments in code -- if I don't do it I'll forget what I did  :-?

---

### Post by douceur on 2005-07-18
Hey, thanks a lot.  Just what I was looking for.

---

### Post by damonw5 on 2005-07-18
[QUOTE=douceur]Hey, thanks a lot.  Just what I was looking for.[/QUOTE]
 Just so you know, you have multiple terminals. Even when X is open, it is in "terminal 7". Try pressing ALT+CTRL+F1 through ALT+CTRL+F7... You can do all your command-line stuff there. I hope this helps (if you don't already know it) :)

---

### Post by JGJones on 2005-07-18
[QUOTE=Xian]This should work:
```
$ sudo update-rc.d -f gdm remove
```
Or if you prefer...

Use the first command to disable GDM and get a console prompt instead.
Use the second command to enable GDM again.

This way you can basically just toggle it on and off.

```
$ sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
```
$ sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```[/QUOTE]

In Breezy, they have a "Services" GUI window now...give a nice list and a tick/untick box...it's a nice touch, so useful for anyone else wanting an easier way to disable services while using X...roll on October (best feature of Breezy is the flashing notification in taskbar of a window requesting attention)

However naturally if wanting to stop X, then learn the above commands :D

---

