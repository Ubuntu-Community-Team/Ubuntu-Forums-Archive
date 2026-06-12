---
title: "what no root terminal???"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Efwis on 2005-10-13
two things I'm wondering about.

1st no root terminal???? can anyone tell me how to get one on here, when I install my stuff via apt-get that would be a nice thing to have.

2nd, no sudo nautilus or am I missing it how to start it up somewhere???

Please answer ASAP, i need to have at least sudo nautilus to set up my printer

---

### Post by Efwis on 2005-10-13
Never mind I figured it out.

for those new to ubuntu or who did a full clean install here is what i did.

open terminal under applications>accressories then type the following.

```
$ sudo nautilus
```
this will give you the sudo nautilus like you had in Hoary.

```
$ sudo su
password: your password you made
```

this will start root terminal for you. now if I can just figure a way to make them clickable links in Gnome-panel

---

### Post by erikpiper on 2005-10-13
Apps> System Tools> Applications Menu Editor.

This is smeg. 

Scroll down to system tools
Click on Root Terminal

Your root terminal now will show up in the menus. It was simply hidden.

---

### Post by Griffin3 on 2005-10-14
Exactly what I was looking for, as I was trying to restore missing root terminal icon and launcher from hoary that disappeared in breezy.  (that hit all the keywords?)

---

### Post by Wolki on 2005-10-14
No need for a root terminal, just use a normal one and "sudo su" to become root on demand.

---

### Post by Efwis on 2005-10-16
[QUOTE=Wolki]No need for a root terminal, just use a normal one and "sudo su" to become root on demand.[/QUOTE]
personally I do a lot of work in root on my machine, so its just plain easier to have the root terminal at a click of the mouse.

---

### Post by Wolki on 2005-10-19
It depends. I like it better to have just one type of terminal, since then I don't have to choose when opening it whether I want a root one or a normal one, so I have to spend less time and have less chance to start the wrong one by mistake. I often can even just use one of the terminals I already have open :)

Your work flow may vary though.

---

