---
title: "three finger salute"
date: 2006-07-28
forum: Desktop Environments
---

### Post by chris1112 on 2006-07-28
Is there a command that will let you kill an application like the three finger salute on windows? It seems that ubuntu locks up every so often. This manifests itself after I run a multimedia program or games. My computer is fairly fast at 2.8ghz and 1 Gig of ram.

---

### Post by jordilin on 2006-07-28
Open a Console and type
```
ps ax
```
you'll get the pid number, then
```
kill -9 pid
```

---

### Post by tredegar on 2006-07-29
<CTRL><ALT><ESC> will give you a skull-&-crossbones cursor. Click this on any window to kill that window.

<CTRL><ESC> will give you a list of running processes, which you can kill if you wish.

HTH

---

### Post by chris1112 on 2006-07-29
Thanks that is what i was looking for:D

---

### Post by mark2741 on 2006-07-29
This isn't working for me when I try either of these key combinations. Basically any open program windows just lose focus, and my cursor stays the same. 

??

> **tredegar said:**
> <CTRL><ALT><ESC> will give you a skull-&-crossbones cursor. Click this on any window to kill that window.

<CTRL><ESC> will give you a list of running processes, which you can kill if you wish.

HTH

---

### Post by tredegar on 2006-07-30
> This isn't working for me
I think this is a feature of KDE. Maybe you are using gnome?

---

### Post by iamhugeinjapan on 2006-07-30
You can also open a terminal (or use the run program dialog) and type:

xkill

You'll get the skull and cross bones cursor then too.

---

### Post by Lord Illidan on 2006-07-30
> **iamhugeinjapan said:**
> You can also open a terminal (or use the run program dialog) and type:

xkill

You'll get the skull and cross bones cursor then too.

Type ALT+F2 and you'll get the run dialog.

---

