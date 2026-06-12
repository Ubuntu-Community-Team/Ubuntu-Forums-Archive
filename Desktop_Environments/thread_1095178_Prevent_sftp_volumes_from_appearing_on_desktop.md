---
title: "Prevent sftp volumes from appearing on desktop"
date: 2009-03-13
forum: Desktop Environments
---

### Post by chuckh1958 on 2009-03-13
Whenever I browse to an sftp:// URL in nautilus, it automatically adds an icon for the server on the desktop. I don't want it do that. Usually I'm browsing to the server for one piece of information and don't need any sort of persistent connection, and I especially don't want my desktop getting cluttered up with icons that will not be used again. Is there any way to prevent this behaviour?

---

### Post by Nostalos on 2009-03-13
Should only persist during your current session.  Should disappear on next logout/login.

---

### Post by chuckh1958 on 2009-03-13
Thanks. 

Someone on the #ubuntu-desktop IRC channel directed me to gconf-editor which lets you disable showing mounts on the desktop. That works for me. I can still get them from the places menu. The key for the setting is /apps/nautilus/desktop in case anyone else is looking for it.

---

