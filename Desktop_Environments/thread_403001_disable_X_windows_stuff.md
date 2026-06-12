---
title: "disable X windows stuff"
date: 2007-04-06
forum: Desktop Environments
---

### Post by dr.silly on 2007-04-06
ok I tried the beryl and things and it broke my computer now when I start up it says it can't start X, it then switches me to the terminal. I think I've gotten rid of all the beryl stuff with sudo apt-get remove beryl emerald but how do I disable X from the terminal?

---

### Post by taurus on 2007-04-06
Try reconfiguring your X again.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dr.silly on 2007-04-06
I don't want to reconfigure I want to remove
besides I think I removed that package anyway

---

### Post by dr.silly on 2007-04-06
I did 'update-rc.d -f gdm remove'
that worked great but now I boot into the terminal and ctrl alt F7 doesn't work

---

### Post by taurus on 2007-04-06
Because you already removed gdm so it is not running anymore!  If you want to start X again, you have to type

```
startx
```

---

### Post by dr.silly on 2007-04-06
no right after i installed x it didn't work so I googled it and it told me to do that but now I boot into the terminal

---

### Post by taurus on 2007-04-06
```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by dr.silly on 2007-04-06
still the same error

---

