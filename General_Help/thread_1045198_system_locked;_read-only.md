---
title: "system locked; read-only"
date: 2009-01-20
forum: General Help
---

### Post by Stargazer989 on 2009-01-20
ok, so i turn on my laptop this morning and THE SYSTEM IS LOCKED IN READ-ONLY or something... [*photo*]("http://adam.pcriot.com/r/100_0103.JPG"). i couldn't write it all down... has anyone had this problem before and has a fix or does anyone know an answer ?

---

### Post by taurus on 2009-01-20
Did you install Ubuntu on it own partition and what filesystem did you use?

---

### Post by Stargazer989 on 2009-01-20
I installed Ubuntu about a month ago on an ext3 partition of 25gB. I've been using it since then...

OK, i've got it: i edited 3 files... in /etc/init.d and /etc/udev/rules.d/

is there a way i could reinstall the files(some generic ones) and do something to make them settle into my current config.. or something. O.O
these are the files:> 
/etc/init.d/mountkernfs.sh
/etc/init.d/mountdevsubfs.sh
/etc/udev/rules.d/40-permissions

---

### Post by taurus on 2009-01-20
When you edit a file with gedit, there is a backup file with the same name with a ~ at the end.

```
ls -la /etc/init.d/mount*
ls -la /etc/udev/rules.d
```

---

### Post by Stargazer989 on 2009-01-20
but is it the original ? becuase i edited the files **after** to remove the added stuff...

*** EDIT: i just tried to replace them and reboot... no luck. is there a way to replace them using another copy ?

---

