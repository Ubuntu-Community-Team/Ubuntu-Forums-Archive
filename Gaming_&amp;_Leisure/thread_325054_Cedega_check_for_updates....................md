---
title: "Cedega: check for updates..................."
date: 2006-12-24
forum: Gaming &amp; Leisure
---

### Post by xenoalien on 2006-12-24
I try to update Cedega and it freezes! Anyone know how to fix this?

---

### Post by xenoalien on 2006-12-24
nevermind... I fixed it with a local update...

---

### Post by baLes on 2006-12-25
Where did you find the local update? I seem to have them same problem.

---

### Post by Demon012 on 2006-12-31
I had the exact same problem but after some searching I found this thread on the Transgaming Forums.

[http://transgaming.org/forum/viewtopic.php?t=7288](http://transgaming.org/forum/viewtopic.php?t=7288)

To save you looking around for ages here is the commands you need to run to get it working properly:

```

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

```

Anyway hope this helps some people,

Demon012

---

### Post by OffHand on 2006-12-31
> **Demon012 said:**
> I had the exact same problem but after some searching I found this thread on the Transgaming Forums.

[http://transgaming.org/forum/viewtopic.php?t=7288](http://transgaming.org/forum/viewtopic.php?t=7288)

To save you looking around for ages here is the commands you need to run to get it working properly:

```

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

```

Anyway hope this helps some people,

Demon012

That's too radical. Fix only Cedega using this code in the terminal.
```
sudo find /usr/lib/transgaming_cedega -type f -exec perl -pi -e "s=/bin/sh=/bin/bash=g" {} \;
```

---

