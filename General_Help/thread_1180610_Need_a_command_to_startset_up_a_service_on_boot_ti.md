---
title: "Need a command to start/set up a service on boot time"
date: 2009-06-07
forum: General Help
---

### Post by colau on 2009-06-07
Hi,
Is there any command to start/set up a service from boot time?
Like in Fedora
```

chkconfig network on

```

---

### Post by sahabcse on 2009-06-07
command is update-rc.d

for more info [http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

---

### Post by sahabcse on 2009-06-07
command is update-rc.d

for more info [http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

---

### Post by colau on 2009-06-12
Thanks.

---

### Post by blackxored on 2009-06-12
I think update-rc.d is rather unflexible if you like chkconfig easy to use. I normally use sysv-rc-conf.
```

sudo apt-get install sysv-rc-conf

```

---

### Post by colau on 2009-06-12
> **blackxored said:**
> I think update-rc.d is rather unflexible if you like chkconfig easy to use. I normally use sysv-rc-conf.
```

sudo apt-get install sysv-rc-conf

```
Thank you.

---

