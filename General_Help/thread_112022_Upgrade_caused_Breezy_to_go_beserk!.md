---
title: "Upgrade caused Breezy to go beserk!"
date: 2006-01-03
forum: General Help
---

### Post by jhoderd on 2006-01-03
Hi,

Something very weird happened: my system was working
perfectly before, but suddenly it has gone bananas (it freezes
when accessing USB storage devices, for example).

Only two things happened in between:

  - I upgraded the system (including new kernel)
  - I have installed KDE 3.5 from kubuntu.org

Now, the problems seems to be USB related, so I suspect
that the kernel transition from 2.6.12-9-386 to 2.6.12-10-386
might be the culprit -- does anyone else report any problems?

The other possibility is that KDE 3.5 somehow messed up things,
in which case my question is: how do I get rid of all the packages
installed from kubuntu.org and go back to vanilla breezy?

Thanks in advance for your help!
Jean Hoderd

P.S.  I can provide more detailed information about the weird
         things happening, if necessary.

---

### Post by jhoderd on 2006-01-03
Hi,

Just one more thing: I would expect that a new USB mass storage
device would show up as /dev/sda.  However, sometimes it appears
as /dev/sdb, though there is no /dev/sda!  Is this normal?

Jean

---

