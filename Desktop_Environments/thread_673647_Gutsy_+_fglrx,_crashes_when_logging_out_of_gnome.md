---
title: "Gutsy + fglrx, crashes when logging out of gnome"
date: 2008-01-20
forum: Desktop Environments
---

### Post by samosamo on 2008-01-20
On a new Gutsy install with manually installed ATI Catalyst 8.1 drivers, gnome will crash when you are logging out or using CTRL+ALT+BACKSPACE.  I tried doing "/etc/init.d/gdm stop" and that crashes in the same fashion.  The only thing I'm able to do is CTRL+ALT+DEL to restart.  I can't log into another console with CTRL+ALT+F1/F2/etc, or anything.  This didn't happen until I installed the new fglrx drivers.

I'd really like to see the X log while its crashing but its impossible.  I had this idea:

> sudo screen tail -f /var/log/Xorg.0.log >> ~/X.txt"

but it didn't work, anyone know how to write that line so it writes to a file ?

---

### Post by samosamo on 2008-01-20
Its a widespread bug with Catalyst 8.1 drivers.  Yay, ATI

[http://www.phoronix.com/forums/showpost.php?p=22838&postcount=47](http://www.phoronix.com/forums/showpost.php?p=22838&postcount=47)

---

### Post by Saint Angeles on 2008-01-21
i can only get my compiz working when i use the 7.11 catalyst driver from november 07.

the newest one dont work.

---

