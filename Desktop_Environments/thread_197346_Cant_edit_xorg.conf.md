---
title: "Cant edit xorg.conf"
date: 2006-06-15
forum: Desktop Environments
---

### Post by smoove on 2006-06-15
Hi there, Im fairly new to Linux and I've been following the guide to get install my nvidia drivers, which worked great, but when It came to editing xorg.conf to add some extra resolutions, i wasnt able to, because I think im currently using it (nvidia logo did load up), so how do I go about edditing a file im already in?

---

### Post by murph2481 on 2006-06-15
did you try typing 'sudo gedit xorg.conf' ?

---

### Post by taurus on 2006-06-15
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak <-- make a back up in case you screw it up.  You can use the original version again...
sudo gedit /etc/X11/xorg.conf <-- now, edit to whatever you want...

```

---

