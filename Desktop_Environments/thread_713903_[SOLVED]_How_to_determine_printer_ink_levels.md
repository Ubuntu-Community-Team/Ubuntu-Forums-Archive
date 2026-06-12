---
title: "[SOLVED] How to determine printer ink levels?"
date: 2008-03-03
forum: Desktop Environments
---

### Post by keratos on 2008-03-03
Hi

My EpsonR800 ink cartridge light is blinking. One of the cartriges needs replacing but I dont know which one. 

On Windows, the printer drivers would tell me which ink was low using colour bars.

However I now use Ubuntu 7.10 and cannot see where this information is obtained. how does/can ubuntu tell me which ink to replace?

Thanks.

---

### Post by ajgreeny on 2008-03-03
Install mtink from repos and then add yourself to the group lp.  Now when you open mtink you will get a gui looking like this attachment.  If you are not in the right group it will only work as root (sudo mtink), but adding yourself to "lp" will get it working as user.  It also allows you to check and if needed, clean the nozzles.

---

### Post by keratos on 2008-03-03
ajgreeny, thanks very much.

I have installed and resolved the issue.

---

