---
title: "How can I tell what is causing start up to hang"
date: 2009-08-06
forum: Desktop Environments
---

### Post by warby1212 on 2009-08-06
Hi, Have just installed 9.04 on my desktop but the start up hangs every time for about 2 minutes with the progress indicator about 20% in. How can I tell what it is hanging on? There are no messages on start up giving any other clues.

---

### Post by warp99 on 2009-08-06
When the computer starts to boot and the "Grub Loading" line appears press escape to get to the grub menu. At that point the default kernel will be highlighted. Press 'e' to edit and highlight the line "kernel". Press 'e' again and remove the words "quiet" and "splash" at the end of the line. Press escape again, then 'b' for boot. Now you can view the boot messages with the splash screen removed. On the next reboot your splash screen will be back to normal since the edit is only for the current session.

---

### Post by warby1212 on 2009-08-06
Thank you very much. I miss the boot messages, Now I can see what's happenning! Great stuff :D

---

