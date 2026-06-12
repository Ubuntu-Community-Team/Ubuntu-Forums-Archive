---
title: "Interesting permissions problem"
date: 2006-09-02
forum: Desktop Environments
---

### Post by autocrosser on 2006-09-02
Created another Ubuntu install on another drive by copy/paste from my root user. The "new" install is a clone of the old install--I have tried various ways before (.tar my drive & untar into another partition after chrooting into it--installing a "basic" & adding the differences between to the new install)

In any case, the "new" install works very well except for permissions for my removable drives. I repaired sudo & modified fstab for user--booted recovery & did chmod 4111 sudo then chmod 4111 pmount---I still need to sudo mount & eject to use the drives--once mounted I can use them as my regular user--everything else works normally but this one is excaping me.

---

