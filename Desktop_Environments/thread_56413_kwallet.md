---
title: "kwallet"
date: 2005-08-12
forum: Desktop Environments
---

### Post by coolclassic on 2005-08-12
Kwallet nolongers responds with passwords. I now get the normal kde prompt when entering a password required web site. Is there any way to restore kwallet.after checking It appears kwallet is empty.

---

### Post by incinerator on 2005-08-15
I had the same problem after an update. Recently, glibc (the package in question is called libc6) has been upgraded and that seems to have upset kwallet and possibly other apps, too.
Reboot and everything should be fine, at least it was for me.

---

### Post by coolclassic on 2005-08-15
It still works for other users but not for me. Kwallet still has all the passwords.

---

### Post by incinerator on 2005-08-15
[QUOTE=coolclassic]It still works for other users but not for me. Kwallet still has all the passwords.[/QUOTE]

Does that mean you can actually see any wallets in the main kwallet window?
If you, check that other apps are actually allowed to access the wallet. This can be found in the kwallet settings (2nd tab).
Also, make sure there is a default wallet selected in the first tab of the kwallet settings window, that it is actually enabled etc.

Apart from that, it may be useful to run kwallet from a console to see if there is any error messages.

Regards,
Dominik

---

### Post by QettoE on 2006-02-12
My Wallet start if I run it from console, but I lost my icon and it does not start when it has to.... any ideas?

---

