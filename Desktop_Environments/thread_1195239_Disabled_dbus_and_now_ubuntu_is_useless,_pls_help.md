---
title: "Disabled dbus and now ubuntu is useless, pls help"
date: 2009-06-23
forum: Desktop Environments
---

### Post by talego on 2009-06-23
Trying to improve security I disabled several services and all went fine until I disabled dbus (also disabled avahi-daemon previously). My ubuntu 9.04 boots but I get some error regarding HAL and Gnome, plus the keyboard and trackpad don't seem to work. Is there any idiot proof way to enable it again? Thanks in advance.

PS: I've been sent this hint but can't find a rescue mode on the ubuntu cd.
```
In rescue (from the cd or dvd) you would run from the command line (as root):
update-rc.d dbus defaults
```

---

### Post by talego on 2009-06-24
Could someone pls lend me a hand with this? cheers,

---

### Post by ~sHyLoCk~ on 2009-06-25
I'm not sure but use the live cd and check out your /etc folder where you will find rc.2 , rc.3 , etc. Try to tweak and see if you can get it back.

---

### Post by talego on 2009-06-26
~sHyLoCk~ could you please be more specific as to what I need to change? cheers,

---

