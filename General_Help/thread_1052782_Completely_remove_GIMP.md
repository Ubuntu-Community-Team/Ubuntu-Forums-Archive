---
title: "Completely remove GIMP"
date: 2009-01-28
forum: General Help
---

### Post by fatnic388 on 2009-01-28
Hi. How can I completely remove GIMP so I can install a fresh copy? I'm trying to install GIMP 2.6.3 in 8.10 but even though the output shows GIMP 2.6.3 package installing GIMP -v shows 2.2.11.

---

### Post by geirha on 2009-01-28
Sounds like you may have two installs of gimp. What does this command say? ```
type -a gimp
```

---

### Post by fatnic388 on 2009-01-28
OK. Done that.
```
dave@laptop:~$ type -a gimp
gimp is /usr/local/bin/gimp
```

---

### Post by geirha on 2009-01-28
Do you remember how you installed gimp under /usr/local? have you built it yourself, installed it with a script, or installed it via a .deb-package?

Does this give any results?
```
dpkg -S /usr/local/bin/gimp
```

---

### Post by fatnic388 on 2009-01-28
SUCCESS!!!
```
dave@laptop:~$ dpkg -S /usr/local/bin/gimp
gimpshop: /usr/local/bin/gim
```
So I removed gimpshop and installed GIMP. Now upto 2.6.3.

Thanks everyone!!!

---

