---
title: "Boot woes: / not remounted as rw"
date: 2007-05-09
forum: Desktop Environments
---

### Post by louis_nichols on 2007-05-09
Hi everybody!

Apparently, I wasn't happy with the way my system was working (perfectly, that is), so I had to screw something up.

Here's the thing. When I boot the system, for an unknown reason, it won't remount the root fs as rw, as it should. This means I have to manually remount it, then assign permissions to /dev/null and /dev/zero and only after this can I use the system properly.

I'm pretty sure this was caused by my using webmin to try and tweak the boot services, but I can't seem to be able to undo it. I can't say I've tried everything yet, but I'm thinking osmeone can help me get out of this trial and error loop.

The problem might also have been caused by my installing eiciel to try and have a go at the more versatile ACL (I only read afterwards that ACL and reiserfs can make an unhappy couple). But my best bet is still on the boot services.

Any help in this matter will be greatly appreciated.

EDIT: forgot to mention my fstab entry looks like this:
```
/dev/mapper/kubuntu-root /               reiserfs defaults        0       1
```

---

### Post by louis_nichols on 2007-05-10
Anyone?

I don't want to have to reinstall the system. I agree it would be a good moment to upgrade to Feisty, but not like this... :)

---

