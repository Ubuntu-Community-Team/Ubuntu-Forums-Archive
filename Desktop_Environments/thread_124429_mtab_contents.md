---
title: "mtab contents"
date: 2006-02-01
forum: Desktop Environments
---

### Post by mefsupport on 2006-02-01
Can anyone explain the following entry in /etc/mtab?

tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0

---

### Post by Ramses de Norre on 2006-02-01
I have exactly the same line in mine, is it causing troubles?
It looks like it has something to do with the kernel.

---

### Post by mefsupport on 2006-02-01
[QUOTE=Ramses de Norre]I have exactly the same line in mine, is it causing troubles?
It looks like it has something to do with the kernel.[/QUOTE]
It's not causing problems per se, however, it does show up in the chkrootkit results, so I'm wondering if its a false positive or if its something I should be worried about.

---

### Post by mefsupport on 2006-02-05
Does no one know anything about this?

---

### Post by bartbes on 2006-02-05
I do, it is actually a dir like /tmp it's memory (virtual or not) mounted there, and at the next bootup it's clean again, it's really nothing to worry about, actually I made an HOWTO on how to mount a tmpfs :p

---

### Post by mefsupport on 2006-02-06
[QUOTE=bartbes]I do, it is actually a dir like /tmp it's memory (virtual or not) mounted there, and at the next bootup it's clean again, it's really nothing to worry about, actually I made an HOWTO on how to mount a tmpfs :p[/QUOTE]
Thanks!

---

### Post by sergio.callegari on 2006-02-16
But do you know why is it there in principle and what is it purpose?
Distributions that are not debian derivatives seem not to have it.

Furthermore, being a tmpfs it uses precious RAM, so it would be interesting to know if it is indispensible to have it...

Finally... does anybody know when it gets mounted?
I have found no trace of it in the init.d files...

---

