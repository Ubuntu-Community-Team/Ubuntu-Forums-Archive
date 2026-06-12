---
title: "recover lost+found data?"
date: 2009-04-08
forum: General Help
---

### Post by anon0 on 2009-04-08
I have files in the lost+found folder of my ext3 RAID volume that I wish to access. I'm trying to copy the files in Nautilus but after I copy I can't seem to paste elsewhere. How are you supposed to access these files?

---

### Post by Tim Sharitt on 2009-04-08
You will likely need administrator privileges to copy or access the file.

You can either use sudo from a terminal or open nautilus as root.

To open nautilus as root, hit Alt-F2 or open a terminal and enter
```
gksu nautilus
```
and enter your password when prompted.

---

### Post by benj1 on 2009-04-08
> **Tim Sharitt said:**
> You will likely need administrator privileges to copy or access the file.

You can either use sudo from a terminal or open nautilus as root.

To open nautilus as root, hit Alt-F2 or open a terminal and enter
```
gksu nautilus
```
and enter your password when prompted.

just out of curiosity whats the difference between

```
gksu nautilus
```
and
```
sudo nautilus
```

ive always used the latter?

---

### Post by anon0 on 2009-04-08
that worked, thanks...

---

### Post by Tim Sharitt on 2009-04-08
> **benj1 said:**
> just out of curiosity whats the difference between

```
gksu nautilus
```
and
```
sudo nautilus
```

ive always used the latter?

See: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by benj1 on 2009-04-08
> **Tim Sharitt said:**
> See: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

thanks i already googled it

---

