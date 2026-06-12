---
title: "Permission denied to file I own with perm 0777 (command 'rm')"
date: 2012-02-11
forum: Desktop Environments
---

### Post by snowweb on 2012-02-11
I've been using my install for the last 2 years but suddenly, I can't delete files!

```
peter@ubuntu:~$ rm /home/peter/Documents/website/bg.png

rm: remove regular file `/home/peter/Documents/website/bg.png'? y

rm: cannot remove `/home/peter/Documents/website/bg.png': Permission denied

peter@ubuntu:~$ ls -la /home/peter/Documents/website/bg.png 

-rwxrwxrwx 1 peter peter 3096 2012-01-22 04:33 /home/peter/Documents/website/bg.png
```Can anyone shine some light on what could be happening here please?

Thanks.

---

### Post by savanna on 2012-02-11
You could try doing the rm with sudo, but that doesn't explain why *you* can't remove it...

---

### Post by snowweb on 2012-02-11
> **savanna said:**
> You could try doing the rm with sudo, but that doesn't explain why *you* can't remove it...

This is true, but I need to solve the problem. This is sure to cause problems throughout if assuming this is not the only file effected.

---

### Post by snowweb on 2012-02-11
Sorry guys.. stupid me! The directory didn't have write permissions. Sorted now.

---

