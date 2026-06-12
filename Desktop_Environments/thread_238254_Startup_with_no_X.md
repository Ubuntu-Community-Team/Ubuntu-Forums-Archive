---
title: "Startup with no X"
date: 2006-08-17
forum: Desktop Environments
---

### Post by cazz on 2006-08-17
I have read some thread here but I dont now if I understand everything.

some say use sysv-rc-conf (but to what?) and some say edit runlevel in /etc/inittab to some number but where and what number?

I have a old computer that I like to run Xubuntu on but I dont want Xfce4 to autostart.

I want so that start in terminal mode because sometime I dont need Xfce4.

So when I startup my computer I have to login in terminal and if I want to run Xfce4 I just write xstart (or what I have to write).


I have install xubuntu 6.06.1

---

### Post by lupine_nickt on 2006-08-17
Change the runlevel in /etc/inittab to 3

The command to start x is, erm, "startx" :D

xF,

...Nick

---

### Post by cazz on 2006-08-17
hehe thanks but what line are I going to have to change?

/EDIT
I change 
```
id:2:initdefault 
```

to 

```
id:3:initdefault 
```

but XFCE4 startup anyway

---

### Post by taurus on 2006-08-17
He meant this in /etc/inittab...

```

id:2:initdefault:

```

---

### Post by cazz on 2006-08-17
mm yes but XFCE4 start anyway

---

### Post by taurus on 2006-08-17
> **cazz said:**
> 
I change 
```
id:2:initdefault 
```

to 

```
id:2:initdefault 
```

Look at those two lines again and tell me where did you change it!!!  ](*,) 

Do you happen to have gdm running?  What is the output of this command from a terminal then?

```

ls -la /etc/init.d

```

---

### Post by Ramses de Norre on 2006-08-17
Runlevels 2-5 are identical when you don't change them your own and all have GDM or KDM loaded at startup.
You'll need to use sysv-rc-conf and deselect gdm or kdm (whichever you use) for the runlevel you boot in (by default 2 but you've set it to 3 now).

---

### Post by cazz on 2006-08-17
Ahhh thanks

I install that and change nr3 so now it works :)

---

