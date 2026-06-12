---
title: "Kdesu and keep root session"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Frunktz on 2006-10-06
There is a way to keep for some minutes the root session instanced by kdesu?
Example: 

```

- kdesu kwrite
<input my password>
- use kwrite as root
- close kwrite
after 1 sec
retype:
- kdesu kwrite
- avoid to retype my password

```With sudo that already works, I can type sudo without retype password for about 5 minutes...For kdesu?

Thanks

---

### Post by Frunktz on 2006-10-11
Any solutions?

---

### Post by aysiu on 2006-10-11
Actually, it should work with *kdesu* too in theory.

I suppose if you're running into this problem repeatedly, you should consider filing a bug report on it.

Alternatively, you can do ```
sudo -i
kwrite
``` in the terminal and then keep launching applications from there as root until you're done.

---

### Post by mexlinux on 2006-10-11
It's a KDE problem, ther is alreadu a bug:
[https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27075]("https://launchpad.net/distros/ubuntu/+source/meta-kde/+bug/27075")
Please comment on it.

---

### Post by Frunktz on 2006-10-12
Thanks for the reply, but that's don't seems a bug because kdesu always start and execute the program, but a missing feature...

Ps:- there's a new version of KDE, 3.5.5. Now that version include support for sudo in kdesu. In Efty we can see Kde 3.5.5 or a precedent version? The new version seems to be a bugfix release...

Sorry for my bad bad English :)

---

