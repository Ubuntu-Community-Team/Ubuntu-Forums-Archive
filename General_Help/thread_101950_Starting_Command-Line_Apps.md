---
title: "Starting Command-Line Apps"
date: 2005-12-11
forum: General Help
---

### Post by fontosaurus on 2005-12-11
I'd like to make some changes so that I can get Ubuntu to automatically start Apache2 and MySQL, both as I log in.  Anyone have any ideas on how to go about this?   :confused:

---

### Post by aysiu on 2005-12-11
System > Preferences > Sessions > Startup Applications?

---

### Post by fontosaurus on 2005-12-11
[QUOTE=aysiu]System > Preferences > Sessions > Startup Applications?[/QUOTE]

Yeah, that was it.  I'm a bonehead.  ](*,)

---

### Post by arpunk on 2005-12-11
[QUOTE=fontosaurus]I'd like to make some changes so that I can get Ubuntu to automatically start Apache2 and MySQL, both as I log in.  Anyone have any ideas on how to go about this?   :confused:[/QUOTE]
I thought apache and mysql start with the system, in fact they *should* do it. Check if you have them on */etc/init.d/* and they both have executable flags.

---

