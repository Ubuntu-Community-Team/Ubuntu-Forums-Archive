---
title: "Cannot Ctrl+Alt+Fn to tty consoles"
date: 2009-04-22
forum: General Help
---

### Post by nikolaiortiz on 2009-04-22
Hi..
I compile a new kernel
and after that Cannot Ctrl+Alt+Fn to tty consoles
is really annoying
can help me ?

---

### Post by KeyserSoze93 on 2009-04-22
Can you change consoles by openning a term and typing:
```
sudo chvt 1
``` (or any other number)?

If you can, I'm not sure how to reenable using the shortcut, but at least if proves they work...

---

### Post by nikolaiortiz on 2009-04-24
Hi KeyserSoze93 
wel using
```
sudo chvt 1
```
doesn't work but if I up to root first
```

sudo su
chvt 1

```
works fine :)
thanx but I use the ttys when my system crash to kill the application and other stuff ..I know is not the best use for a tty but I'm a noob :P
so any ideas why I lost mi ctrl+del+F ?

I restart my laptop and walllaaaaa!! my ttys are back
I don't know if chvt change some in my configuration but well, now all works :)
SOLVED!!!!

---

