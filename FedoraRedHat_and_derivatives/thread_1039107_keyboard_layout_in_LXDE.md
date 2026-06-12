---
title: "keyboard layout in LXDE"
date: 2009-01-14
forum: Fedora/RedHat and derivatives
---

### Post by mhh91 on 2009-01-14
i'm using fedora 10 and i've just installed LXDE,everything is going okay,but i can't switch my keyboard layout to any other language,just english is there,can somebody help me with that please?

---

### Post by matata on 2009-01-29
I couldn't find a good solution, but this command line seems good enough (at least for me):
```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar
```
It's for Arabic, English switching using both Alt+Shift
and it works :D

---

### Post by mhh91 on 2009-02-12
> **matata said:**
> I couldn't find a good solution, but this command line seems good enough (at least for me):
```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar
```
It's for Arabic, English switching using both Alt+Shift
and it works :D

thanks :D

i'll give it a try :)

---

### Post by mhh91 on 2009-02-12
it DID work :D


thanks a lot :)

---

