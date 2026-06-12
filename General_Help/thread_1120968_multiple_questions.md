---
title: "multiple questions"
date: 2009-04-09
forum: General Help
---

### Post by neon100 on 2009-04-09
QUESTION 1
When booting... somewhere in between all the text that appears before the login screen.. a line appears saying 'FILE SYSTEM IS NOT CLEAN'. Why is it NOT CLEAN? How can i CLEAN it?

QUESTION 2
Is there any ubuntu software that helps me defrag the reiserFS partition or scan it for errors to tweak it for better performance?

---

### Post by DeMus on 2009-04-09
> **neon100 said:**
> QUESTION 1
When booting... somewhere in between all the text that appears before the login screen.. a line appears saying 'FILE SYSTEM IS NOT CLEAN'. Why is it NOT CLEAN? How can i CLEAN it?

QUESTION 2
Is there any ubuntu software that helps me defrag the reiserFS partition or scan it for errors to tweak it for better performance?

Question2: I don't know exactly how it works but it seems a Linux disc does not need to be de-fragmented since it will not be fragmented.

---

### Post by lykwydchykyn on 2009-04-09
It is not clean when it has not been shut down properly.  It should "clean" itself on boot, but you will get this message if the machine was not properly shutdown.  If you get this message every time, and you shutdown normally, it could be a problem with the way your system is shutting down.

---

### Post by neon100 on 2009-04-09
> **lykwydchykyn said:**
> It is not clean when it has not been shut down properly.  It should "clean" itself on boot, but you will get this message if the machine was not properly shutdown.  If you get this message every time, and you shutdown normally, it could be a problem with the way your system is shutting down.


Yes its written there every time i boot up even after proper shutdown.

---

### Post by The Cog on 2009-04-09
Then you could try and clean it from a live CD. Use **df -h** to list your partitions and find which one is your root, e.g. /dev/sda1 or similar.
From a live CD, run fsck (file system check) like this but using the correct device name:
**sudo fsck /dev/sda1**

P.S. you can't do it from a system that's running on the drive being checked, which is why you need the live CD.

---

### Post by soltanis on 2009-04-09
Echoing The Cog, you need to check the integrity of your filesystem (and possibly fix it) using the fsck command.

If your system is not shutting down properly (doing this every time, in other words), the next time you shut down, see if anything is being written out to the terminal and check your system logs for anything extraordinary.

---

### Post by neon100 on 2009-04-14
thank you all.... honestly !

---

