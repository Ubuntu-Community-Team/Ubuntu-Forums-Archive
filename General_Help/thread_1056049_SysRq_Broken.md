---
title: "SysRq Broken"
date: 2009-01-31
forum: General Help
---

### Post by Unanimated on 2009-01-31
Today, I had my first kernel panic. I know these can be fixed by the Magic SysRq keys, but no. I had to do a hard reset because they don't work. Why don't they?

EDIT: Okay, apparently they can't be fixed by SysRq, but I still want them to work.

---

### Post by Alterax on 2009-02-13
Raising Elephants Is So Utterly Boring...that's how I remember the sequence of the magic SysRq keys, (CTRL-Alt-SysRQ-REISUB) for the uninitiated.

The problem is that they aren't made to fix kernel panics; they're written into the kernel as a means of having a handy escape hatch if the OS won't respond at all.

My question is what brought on the Kernel panic?  What were you doing when it happened?  Or for that matter, what recent changes have you made to the kernel or the initrd image?  That could help us get to the bottom of this.

---

