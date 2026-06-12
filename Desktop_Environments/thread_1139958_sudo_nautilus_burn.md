---
title: "sudo nautilus burn:/// ?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by markjreed on 2009-04-27
I'm trying to create a CD backup of system files, which means I need to run CD/DVD Creator as root.  But when I run the command in the subject line, I get a message that nautilus cannot handle 'burn:' locations.  

If I run nautilus without sudo (either as myself, or as root if I've logged in as root in the first place), it can handle burn: locations just fine.  So what's missing from or different about the environment when I run it via sudo (or gksudo)?  How can I enable this functionality?

I've searched for this problem and the only reference I found said that an extra installation of gvfs was to blame, but that's not the case here.

---

### Post by mcduck on 2009-04-27
How about creating a tar.gz archive of all the stuff you need to backup (as root) and then burning the archive to disk as normal user?

Files and directories will keep their ownerships & permissions when compressed into tar.gz or tar.bz archives.

---

