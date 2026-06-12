---
title: "Trouble installing ccsm"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by polishpolak on 2007-11-09
I just switched from xp to ubuntu, and I'm having a lot of trouble.

Im trying to install ccsm, but wen I do "sudo apt-get install compizconfig-settings-manager
" it tells me "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

What am I supposed to do? 

When I type dpkg --configure -a in the terminal, it tells me: "dpkg: requested operation requires superuser privilege
" ?!?

Thanks

---

### Post by Zorael on 2007-11-09
Just add sudo to the beginning of it.

```
$ sudo dpkg-reconfigure --configure -a
```

It doesn't sound like an error you should be encountering, though.

---

### Post by polishpolak on 2007-11-09
thank you very much for the fast reply

---

### Post by polishpolak on 2007-11-09
thank you very much for the fast reply

---

