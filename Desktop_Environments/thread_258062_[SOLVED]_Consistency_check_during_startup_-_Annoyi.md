---
title: "[SOLVED] Consistency check during startup - Annoying..."
date: 2006-09-15
forum: Desktop Environments
---

### Post by wieman01 on 2006-09-15
Does anybody know how to reduce the frequency of those annoying HD consistency checks that Ubuntu performs during startup after having booted the for 20 times or so? What file controls that?

---

### Post by marianom on 2006-09-15
There's this guy who posted a method to run the check whenever you want. It was no long ago (less than 2 months). I'm trying to find the post to link it here with no success yet.
I'll keep looking.

---

### Post by mitch.c on 2006-09-15
> **wieman01 said:**
> Does anybody know how to reduce the frequency of those annoying HD consistency checks that Ubuntu performs during startup after having booted the for 20 times or so? What file controls that?

I believe it's actually written into the filesystem (ext2/3). To change to something like 50, you could run:
```
# Replace /dev/partition appropriately
# Replace 50 with new count or 0 to disable
sudo tune2fs -c 50 -i 0 /dev/partition
```
But please man tune2fs and review warnings before you do this!!

---

### Post by wieman01 on 2006-09-15
Thank you. Have been looking for this command for a while. Tested it and it does its job well. 

No, I won't disable the checking after reading the "man pages".

---

### Post by Odinist on 2006-09-15
Ha, annoying? Try playing around with your Win install, hosing it with spyware (and I mean like, seriously... hosing the crap out of it, because that's funny. ^_^ ), and then whenever you boot into Linux, the file checker is going through the HD that your Win install is on, and freaking out because there are SO MANY discrepancies.

Hehehe. ^_^ Good times.

---

