---
title: "Debian xfce"
date: 2008-12-28
forum: Debian
---

### Post by NaF on 2008-12-28
prolly a dumb question.
Installed the latest stable netinst-debian and chose just the basesystem. Arriving at the terminal i:
```

# su
# aptitude update
# aptitude install xfce4

```
It installed all and well. But how do I start it :oops:

---

### Post by exploder on 2008-12-28
I might be wrong but I think you need to install either gdm or kdm so you have a display manager.

---

### Post by kerry_s on 2008-12-28
make sure you install xorg to.

just type> startx

---

### Post by NaF on 2008-12-29
> **kerry_s said:**
> make sure you install xorg to.

just type> startx

```

# X: Cannot stat etc/X11/X (No such file or directory, aborting
# xinit:  Connection refused (errno 111):  unable to connect to X server
# xinit:  No such process (errono 3):   Server error

```
It actually says "stat" and not start, which I think it means, but that's the output I get when I type in ```
startx
```

---

### Post by kerry_s on 2008-12-29
that's because you did not install xorg.

```
sudo apt-get install xorg
```

---

### Post by NaF on 2008-12-29
Thank you very much :)
So to install xfce on a debian:
```

# su
# aptitude update
# aptitude install xfce
# aptitude install gdm 
# aptitude install xorg
# startx

```

for future reference

---

### Post by kerry_s on 2008-12-30
> **NaF said:**
> Thank you very much :)
So to install xfce on a debian:
```

# su
# aptitude update
# aptitude install xfce
# aptitude install gdm 
# aptitude install xorg
# startx

```

for future reference

you can just put it in 1 line:
```

su
apt-get install xorg gdm xfce4
exit
startx

```

you'll want to exit root(su) before you startx

---

