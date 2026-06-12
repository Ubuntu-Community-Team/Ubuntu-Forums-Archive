---
title: "Synaptic stuck on &quot;processing triggers for man-db&quot;"
date: 2009-05-10
forum: General Help
---

### Post by Rackstar on 2009-05-10
Hi,

Since I upgraded to Jaunty, I sometimes get that synaptic gets stuck on things like "processing triggers for man-db".

I don't really know what happens, but it just gets stuck, my whole system is responsive, but it won't move on.

Killing synaptic seems a big no-no to me. What should I do?

The package I'm trying to install now is conky.

Thank u!

---

### Post by spiderbatdad on 2009-05-10
really hard to say, but have you tried reinstalling the package man-db?
usually there would be other errors that follow or a more complete error.

---

### Post by Rackstar on 2009-05-10
No I haven't... I will try to, but for now. Is it safe to kill synaptic? Or should I kill some other process?

---

### Post by Rackstar on 2009-05-10
I killed synaptic. Now when I try to reinstall man-db, I get stuck on:

"Registering documents with scrollkeeper"

---

### Post by spiderbatdad on 2009-05-10
you cant run more than one instance of apt-get or one package manager so you will have to close it. If you encounter a lock in /var/cache/apt/archives, you can remove it.

---

### Post by spiderbatdad on 2009-05-10
how did you upgarade to jaunty? was it by update-manager -d from 8.10 or through multiple distros...like from 8.04->8.10->9.04? Or did you do a clean install? Can you run apt-get update && apt-get upgrade?

---

### Post by Rackstar on 2009-05-10
Killed the little *******, rebooted, reinstalled man-db first, reinstalled conky without any problems.

Thanks!

I hope I'll stop getting those freezes now.

---

