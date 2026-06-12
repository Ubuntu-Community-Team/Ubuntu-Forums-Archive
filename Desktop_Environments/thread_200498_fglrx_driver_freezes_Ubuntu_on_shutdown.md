---
title: "fglrx driver freezes Ubuntu on shutdown"
date: 2006-06-20
forum: Desktop Environments
---

### Post by 3zrael on 2006-06-20
Hi!
What I'm experiencing seems a common issue.
With fglrx driver my system is unable to shutdown properly: it hangs with black screen and nothing more.
It may sound strange but reboot works well... :confused: 
I have a 9600pro and don't want to use Dapper's ATI driver, I get bad 2D and 3D performances.

Could you help?

Thx in advance!

---

### Post by 3zrael on 2006-06-20
Ok, pheraps I solved it!
I uncommented this line

#TerminateServer=true

in this file:

/etc/kde3/kdm/kdmrc


Let's hope it ends here!
:D

---

