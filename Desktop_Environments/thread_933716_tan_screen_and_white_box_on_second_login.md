---
title: "tan screen and white box on second login"
date: 2008-09-29
forum: Desktop Environments
---

### Post by roman5x3 on 2008-09-29
I have a fresh install and on the second login no matter who logged in first and second I get a tan screen and a white box with no border in the top left hand corner.  This always occurs during the second login and all after that.  Rebooting fixes it. Can anyone tell me why this is doing this and how to fix it?

Roman5x3

---

### Post by Deadmode on 2008-10-09
> **roman5x3 said:**
> I have a fresh install and on the second login no matter who logged in first and second I get a tan screen and a white box with no border in the top left hand corner.  This always occurs during the second login and all after that.  Rebooting fixes it. Can anyone tell me why this is doing this and how to fix it?

Roman5x3

having same exact problem except it always comes up with the white box in the top left hand corner.  Tried ctrl+alt+f1 tried to reinstall ubuntu desktop.  Tried to update upgrade.  No success however.  Perhaps a fresh re-install?  I'll post back.

---

### Post by roman5x3 on 2008-10-19
Let me know if the reinstall works.
Roman

---

### Post by Deadmode on 2008-10-19
> **roman5x3 said:**
> Let me know if the reinstall works.
Roman

My problem was GDM was crashing.  The white box was really the box to define the gdm error, but couldn't load.  I jumped into linux shell (ctr+alt+f1).  I found a similar thread that they were getting this gdm error after they had edited their /etc/networking/interfaces.  Which is exactly what I did.  I had a backup on hand and restored the file back to normal.  Everything works fine now.

---

