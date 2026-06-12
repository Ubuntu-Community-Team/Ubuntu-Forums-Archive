---
title: "synaptic suddenly stopped starting when called from menu; works from command line"
date: 2016-11-08
forum: Desktop Environments
---

### Post by corporate-khwilliamson on 2016-11-08
Overnight, the synaptic package manager stopped working when called from System->Administration->Synaptic Package Manager.  However, from a terminal, /usr/sbin/synaptic
 does start it.  On other computers, in earlier Ubuntus, the menu also didn't work, but I didn't try the command line then.  I can't remember if I updated the software to the latest version before or after I used synaptic last.

---

### Post by howefield on 2016-11-08
> **corporate-khwilliamson said:**
> Overnight, the synaptic package manager stopped working when called from System->Administration->Synaptic Package Manager.

Which release are you using ?

```
cat /etc/*-release
```

>  However, from a terminal, /usr/sbin/synaptic does start it.  On other computers, in earlier Ubuntus, the menu also didn't work, but I didn't try the command line then.  I can't remember if I updated the software to the latest version before or after I used synaptic last.

Your apt history.log file should tell you what was updated and when..

```
/var/log/apt/history.log
```

---

