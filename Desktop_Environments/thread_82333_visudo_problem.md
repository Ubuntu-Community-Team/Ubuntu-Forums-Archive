---
title: "visudo problem"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Hallavej on 2005-10-26
Stupid me. I edited /etc/sudoers and now sudo gives me this error:
sudo: parse error in /etc/sudoers near line 22
but of couse I need to run sudo to change the file back to the original.
What can I do?

---

### Post by Xian on 2005-10-26
Boot into recovery mode.
That will drop you into a shell as root.

Do the visudo command again and edit the file.

---

### Post by Hallavej on 2005-10-26
[QUOTE=Xian]Boot into recovery mode.
That will drop you into a shell as root.

Do the visudo command again and edit the file.[/QUOTE]

Of course.
Thanks a lot.

---

