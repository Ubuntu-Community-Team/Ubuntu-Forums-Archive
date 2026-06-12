---
title: "tightvnc"
date: 2008-12-25
forum: Desktop Environments
---

### Post by num on 2008-12-25
hello,

i installed tightvncserver onto my linux box but i cannot find it anywhere in the programs. is this a gui version of the software or what? where to find it?

---

### Post by jrusso2 on 2008-12-25
it probably didn't make the short cut.  You can make one yourself if you can find the executable.

You can try running tightvnc from the terminal and see what it says.

---

### Post by num on 2008-12-25
how can i find where it is located?

---

### Post by num on 2008-12-25
what would it even be called?

---

### Post by obsrv on 2008-12-25
type "t" into terminal and press TAB twice, then you will see a list of programs starting with t, try writing "tigh" and then TAB, if you see tightvnc or it is completed press enter and you have it :)

---

### Post by ugm6hr on 2008-12-25
Do you use Ubuntu / Gnome?

If yes - just use the pre-installed "vino"

To get to GUI config (System->Prefs->Remote Desktop) or:

```
vino-preferences
```

---

### Post by num on 2008-12-25
how do i setup the vnc with remote desktop?

---

### Post by ugm6hr on 2008-12-25
> **num said:**
> how do i setup the vnc with remote desktop?

Tick the boxes you want.

To activate: "Allow other users to view your desktop"

It is pretty obvious from there.

---

### Post by num on 2008-12-25
thats the thing i dont see that though, it just says "view others desktop" and thats it. it doesn't tell me any id or password or anything.

is the remote desktop also vnc?

---

### Post by ugm6hr on 2008-12-25
> **num said:**
> thats the thing i dont see that though, it just says "view others desktop" and thats it. it doesn't tell me any id or password or anything.

In Terminal:
```
vino-preferences
```

If it doesn't work. install it:

```
sudo apt-get install vino
```

You should see this

---

