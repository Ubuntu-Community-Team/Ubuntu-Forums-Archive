---
title: "password missmach"
date: 2012-01-18
forum: Desktop Environments
---

### Post by drumanart on 2012-01-18
Hello,
I tried to make a new user account and I messed up my own user privileges.
Still my old password is accepted when the system asks for the keyring, but I'm not able to use sudo ... so I can't install new software any more.
Is there a way to get to the initial configuration?
Thanks for help.
Martin

---

### Post by nothingspecial on 2012-01-18
Reboot into recovery mode and choose a root shell.

```
passwd user
```

where user is martin or whatever your username is.

```
exit
```

That should fix it.

---

### Post by drumanart on 2012-01-18
Thanks for replying.
I don't see the GRUP menu when booting the computer. How do I get there?
Thanks Martin

---

### Post by raja.genupula on 2012-01-18
Hold your shift key while you're booting your system . that will gives grub menu .

---

### Post by drumanart on 2012-01-19
Thanks a lot

---

### Post by raja.genupula on 2012-01-19
so you got that and solved  you issue ? if yes please mark the thread as solved from thread tools.

Thank you.

---

