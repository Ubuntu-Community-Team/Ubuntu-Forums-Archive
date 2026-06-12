---
title: "Rdesktop no sound with win 2008 r2"
date: 2011-02-25
forum: Desktop Environments
---

### Post by _UsUrPeR_ on 2011-02-25
Hey all. I am having some problems getting rdesktop working with sound. From what I understand, I should be able to use the following to allow sound support:

```
rdesktop -r sound:local [server ip address]
```

I can see that Windows says that it's outputting sound to a "remote audio", but there is no sound. If I connect to the same server with a windows rdp session, everything seems to work great.

Can I get some suggestions?

---

### Post by gradinaruvasile on 2011-02-25
What does 

rdesktop --help

show you as possible audio devices? Under the "available drivers for 'local':" string.

BTW there is xfreerdp now that is rdesktop's continued evolution. It is also integrated in the excellent Remmina graphical remote desktop client.

---

