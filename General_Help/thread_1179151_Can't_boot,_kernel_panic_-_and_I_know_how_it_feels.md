---
title: "Can't boot, kernel panic - and I know how it feels..."
date: 2009-06-05
forum: General Help
---

### Post by Bearly Able on 2009-06-05
Hi,

I've been having problems with frequent random crashes and freezes ever since I upgraded to Jaunty.  I usually have to run fsck afterwards, and it finds various inode problems.

Earlier today, the same thing occurred, and yet again I had to do a hard shutdown.  Now I can't boot at all, even in recovery mode.  The last part of the process went pretty much like this (I had to copy it by hand, so I hope I can read my own writing):
```
Begin Running /scripts/init-bottom...
mount: mounting /dev on /root/dev failed: No such file or directory.
Done.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: mounting /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg

```

I ended up with ```
/init: line 258: cannot open /root/dev/console: no such file.
[305.180681] Kernel panic - not synching: Attempted to kill init!
[305.180729] Dumping ftrace buffer:
[305.180770]       (ftrace buffer empty)
```

Then it sat for ages at a cursor, doing nothing, and I finally had to do a hard restart (again) and boot from the Live CD.

As I don't understand any of the above, I have two main questions:

(1) Is it recoverable, and if so, how?
(2) Even if the answer to the above is 'yes', would I be better doing a fresh install, and possibly going back to 8.04 or 8.10?

I'd be most grateful for any help - I'm going slowly demented over this. :frown:

---

### Post by Bearly Able on 2009-06-06
OK, this seems to be linked to the [bug reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691") to affect 64-bit users.  I've given up and done a fresh install of 8.10 to get a working computer back.

---

