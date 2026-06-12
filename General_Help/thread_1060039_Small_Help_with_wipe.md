---
title: "Small Help with wipe"
date: 2009-02-04
forum: General Help
---

### Post by kyklops on 2009-02-04
Hi everyone,
with the wipe command is all ok. But I don't understand what means that example in the man wipe page:

```
wipe -rfi >wipe.log /var/log/*
Here,  wipe  will  recursively (option -r) destroy everything under /var/log,
excepting /var/log. It will not attempt to chmod() things. It will however be
verbose (option -i). It won’t ask you to type ‘‘yes’’ because of the -f option.
```

In particular I don't understand "destroy everything under /var/log, excepting /var/log"

Perhaps should be "destroy everything under /var/log, excepting /var/log/wipe.log", but so it don't work

Can someone help me?

---

### Post by Fixman on 2009-02-04
> **kyklops said:**
> Hi everyone,
with the wipe command is all ok. But I don't understand what means that example in the man wipe page:

```
wipe -rfi >wipe.log /var/log/*
Here,  wipe  will  recursively (option -r) destroy everything under /var/log,
excepting /var/log. It will not attempt to chmod() things. It will however be
verbose (option -i). It won’t ask you to type ‘‘yes’’ because of the -f option.
```

In particular I don't understand "destroy everything under /var/log, excepting /var/log"

Perhaps should be "destroy everything under /var/log, excepting /var/log/wipe.log", but so it don't work

Can someone help me?

That command destroys everything in /var/log except for the folder /var/log (it will become an empty folder) and write the output to wipe.log.

---

### Post by kyklops on 2009-02-04
Thanks a lot

---

