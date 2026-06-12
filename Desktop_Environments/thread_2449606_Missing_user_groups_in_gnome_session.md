---
title: "Missing user groups in gnome session"
date: 2020-08-30
forum: Desktop Environments
---

### Post by juergen-1 on 2020-08-30
I have a brand new Ubuntu 20 installation with my main user being member of root and also a few other groups like www-data, lp, sudo and others

When I login to Gnome and open a terminal, the user only belongs to the root group.

When I login with ssh to the same host, that user belongs to all assigned groups.

Pulling my hair out on this one and I can't figure out how I could fix that for the regular Gnome session too. Anyone with a suggestion what could be wrong here?

---

### Post by TheFu on 2020-08-30
Run:
```
id

```That is telling the truth for group membership.  I wouldn't trust gnome.
I think adding a userid to the 'root' group would be terrible security. There has to be a better solution to the problem that is trying to solve.

---

### Post by juergen-1 on 2020-08-30
It's interesting though: when a user belongs to root and others, `id` only shows root and none of the others. If the user does not belong to root, then `id` shows them all. That hasn't been like that in Ubuntu 14 and 16 but seems to have been introduced in 18 and is still the same in 20 ofcourse.

---

### Post by SeijiSensei on 2020-08-30
I don't see any reason for ordinary users to belong to the "root" group.  Anyone who needs administrative privileges should be in the "sudo" group.

---

### Post by TheFu on 2020-08-30
> **juergen-1 said:**
> It's interesting though: when a user belongs to root and others, `id` only shows root and none of the others. If the user does not belong to root, then `id` shows them all. That hasn't been like that in Ubuntu 14 and 16 but seems to have been introduced in 18 and is still the same in 20 ofcourse.

There have been a number of deep changes around the cgroups buried inside the kernel the last few years to close some security problems and better sandbox containers.  Tools that used to be setuid, aren't anymore. They get specific cgroup capabilities instead now.  An example: [https://linux-audit.com/linux-capabilities-hardening-linux-binaries-by-removing-setuid/](https://linux-audit.com/linux-capabilities-hardening-linux-binaries-by-removing-setuid/)

---

### Post by juergen-1 on 2020-08-30
Agreed, I had only done so for my own user on personal hardware - for convenience reasons. And up until Ubuntu 16 that had not caused any issues like the described one.

---

