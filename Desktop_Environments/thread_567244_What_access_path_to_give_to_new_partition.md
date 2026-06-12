---
title: "What access path to give to new partition?"
date: 2007-10-04
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-10-04
I just fitted a bigger drive into my Dapper box, and cloned from the old one with Clonezilla. It hasnt given me the extra space, I added the unformatted partition in Disks in the system, but when I choose format, it asks me the access path - default is /boot, is this correct? If I choose /home, will my home directory get the extra space? thats what I want.

---

### Post by happysmileman on 2007-10-04
> **mister_p_1998 said:**
> If I choose /home, will my home directory get the extra space? thats what I want.

Choosing /home would replace your home partition with new one, not add on to it, if you mean you've already cloned your /home partition to it then yeah, but mounting on /home would replace all your current files in /home, which may be what you want as long as you copy everything from your current /home first

---

### Post by mister_p_1998 on 2007-10-04
No, I want to use it as extra storage space, Ive mounted it as /storage, and formatted it, chown'ed it to me, and made a link to it on the desktop. Is there anything else I should do?

---

### Post by happysmileman on 2007-10-04
> **mister_p_1998 said:**
> No, I want to use it as extra storage space, Ive mounted it as /storage, and formatted it, chown'ed it to me, and made a link to it on the desktop. Is there anything else I should do?

Not really, that should work fine for storing things, as long as it's just for storing stuff and doesn't need to be used for anything system-related it doesn't really matter where you mount it.

---

### Post by mister_p_1998 on 2007-10-05
Is there no way I can resize my main partition (which contains /home) to access the extra space without having a separate partition?

---

