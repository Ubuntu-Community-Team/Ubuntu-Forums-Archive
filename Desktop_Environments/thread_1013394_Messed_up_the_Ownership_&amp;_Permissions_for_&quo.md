---
title: "Messed up the Ownership &amp; Permissions for &quot;sudoers&quot; file"
date: 2008-12-16
forum: Desktop Environments
---

### Post by keithld on 2008-12-16
I was trying to edit it and add a line for Firestarter and I had no save option so I changed the ownership to administrator and now I get either an su ID error, "is  owned by uid 1000 should be 0" and the permissions i.e., "mode is 0660, should be 0440"

How can I get this back to default????  I got the mode back to 0440 just need to give permissions back to root...


Thanks guys...

---

### Post by caljohnsmith on 2008-12-16
If you boot into recovery mode, probably all you need to do to fix the problem is:
```
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
```
That should work if the line you added to sudoers doesn't have bad syntax. You should use "visudo" whenever you want to edit sudoers, because it won't let you save sudoers if it has a syntax error. You can use nano with visudo by doing:
```
EDITOR=nano sudo -E visudo
```
Let me know how it goes.

---

