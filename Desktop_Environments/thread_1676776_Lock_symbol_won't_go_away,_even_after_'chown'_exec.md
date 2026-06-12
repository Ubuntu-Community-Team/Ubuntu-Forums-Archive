---
title: "Lock symbol won't go away, even after 'chown' exec."
date: 2011-01-27
forum: Desktop Environments
---

### Post by Moozillaaa on 2011-01-27
I did the chown task, as root, and the file icon still has the lock symbol on it. 

I did it on another file on my desktop just before that, and the symbol went away.

I checked 'Properties', and it shows me as owner. 

It's an ISO on my desktop, copied from LXF Magazine DVD.

Ideas here?

---

### Post by AlphaLexman on 2011-01-27
> **Moozillaaa said:**
> I did the chown task, as root, and the file icon still has the lock symbol on it. 

I did it on another file on my desktop just before that, and the symbol went away.

I checked 'Properties', and it shows me as owner. 

It's an ISO on my desktop, copied from LXF Magazine DVD.

Ideas here?

I believe you are confusing file permissions with file/icon properties. Any file with 'chmod 777 *filename*' can have a lock emblem attached to the icon.

Just adding a lock emblem does not change the permissions of the file, it only gives a graphical representation of what the permissions **might** be.

---

