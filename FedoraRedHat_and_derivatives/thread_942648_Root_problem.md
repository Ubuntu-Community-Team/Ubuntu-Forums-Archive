---
title: "Root problem"
date: 2008-10-09
forum: Fedora/RedHat and derivatives
---

### Post by Rich78 on 2008-10-09
I've made a bit of a boob and not added myself as a sudoer prior to editing the passwd file to prevent root login (ie (/sbin/nologin).

This means I have no way of performing administrative tasks.

Is there a way to fix this other than blowing the box?

The distro is Red Hat 9.

I can't believe I've done this and feel thoroughly stupid.

There may be users on the box with sudoer accounts but I'd rather try to fix this than admit to them what I've done just yet.....

Thanks

---

### Post by bodhi.zazen on 2008-10-09
You can fix it with a live CD.

Mount your Fedora partition and edit the relevant files.

---

### Post by Rich78 on 2008-10-09
I assume any distro live cd will work?

Once mounted, there will be no security wrapped around it and it will be treated like a disk of flat / binary files?

Thanks

---

### Post by jerome1232 on 2008-10-09
Well live cd's allow you to get root privilages with no password. I don't know if fedora has it but in some distro's you can also boot in single user mode which gives you a root shell.

---

### Post by bodhi.zazen on 2008-10-09
Any live CD will do ...

This is why physical security is so critical.

---

