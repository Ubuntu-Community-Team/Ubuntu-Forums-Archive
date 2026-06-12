---
title: "System SUSPEND (to disk &amp; ram) DISABLED after update"
date: 2009-02-15
forum: General Help
---

### Post by fred the wise on 2009-02-15
Hi all!

Today after updating (Kub 8.10) my suspend to disk/ to RAM shutdown options vanished.

(I also had a link in the favourites which now tells: "leave:/suspendram" but doesn't work)

What might be the problem...?
Thanks in advance

---

### Post by shibainucan on 2009-02-16
> **fred the wise said:**
> Hi all!

Today after updating (Kub 8.10) my suspend to disk/ to RAM shutdown options vanished.

(I also had a link in the favourites which now tells: "leave:/suspendram" but doesn't work)

What might be the problem...?
Thanks in advance

The same thing happened to me.  I don't know why.

---

### Post by jynyl on 2009-02-18
Same symptoms here, Kubuntu 8.10.  Update a couple of days ago removed suspend to RAM and suspend to disk options in the Leave menu.

Posted as a bug ...
[https://bugs.launchpad.net/ubuntu/+bug/330848]("https://bugs.launchpad.net/ubuntu/+bug/330848")

---

### Post by sesquipedalianman on 2009-02-20
I have the same problem, but as a workaround, the scripts in /etc/acpi/ seem to work for me.  You have to run them as root or sudo, but sleep.sh has suspended my HP laptop to RAM successfully.

---

### Post by grouch on 2009-03-02
I have the same problem.  As a temporary fix, you can:
```
$ sudo /etc/acpi/sleep.sh 
```

---

