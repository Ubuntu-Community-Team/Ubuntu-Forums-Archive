---
title: "Changing mouse icon theme for applications using qt on a gnome desktop"
date: 2010-05-12
forum: Desktop Environments
---

### Post by ccprog on 2010-05-12
I am using a Gnome desktop with a custom mouse icon theme (a left-hand DMZ white), but inside applications using qt libraries like kaffeine, the mouse icons revert to the default right-hand variant. I have qt-config installed, but there seems to be no option to choose a mouse icon theme. Where do I have to look?

---

### Post by ccprog on 2010-06-20
Self-solved, again.

Create a file ~/.icons/default/icon.theme that contains the following:
```

[Icon Theme]
Inherits=

```
Insert the name of the cursor theme after the "="

---

### Post by cserpentis on 2010-10-27
Man, you saved my day. Had an exceptionally long googling on that issue. Thanks a bunch.

---

### Post by xiaq on 2011-02-10
Thanks for the information. A little complement: on my machine running 10.04.1, creating the file ~/.icons/default/index.theme instead of icon.theme actually solves my problem.

---

### Post by morgengenuss on 2011-11-22
hm, this doesn't work for me in ubuntu 11.10, seems like a strange bug with skype that i never had before and that i can't seem to be able to solve...

---

