---
title: "no free space on the USB stick"
date: 2009-01-05
forum: General Help
---

### Post by Ebeda on 2009-01-05
Greetings to all Ubuntu-friends. I please you for helping me, as I did not discover the question of the full USB flash disc. I have created my modified 8.10 system, which is started from the Flash disc. I wanted to add some files there. When I have started the copying process, I had a "free space" of 1.6 MB. But, the files have occupy more space, what was announced by a message "no free space". Therefore I have delete them, but the space is not more free  - when I click on the "File System", there is still written Free Space: 0 MB. Trash is empty. I have tried any sudo freeall etc., I have tried Klean System - but it has write only some hundreds of kB. Bad is that Windows show me the free space more than 2 GB, but in Ubuntu, there are not functional the bookmarks in Firefox, it is not possible to install anything and the whole system is paralysed and unstable. Could I do something more the newly formate the flash disk and install Ubuntu again? Thanks in advance for any idea.

---

### Post by redilyn on 2009-01-05
Try using the disk usage analyzer to check your usb key and see what is using the space.

It is possible that you have files left in the trash on your usb key.

Try mounting the usbkey in ubuntu, open it in nautilus then press CTRL+H and look for a .trash folder.

---

