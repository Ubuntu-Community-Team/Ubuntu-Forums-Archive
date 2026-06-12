---
title: "hoe to find windows share in fiel system"
date: 2009-05-15
forum: General Help
---

### Post by deanwarren on 2009-05-15
When I use the menu option 'Network' to navigate to a windows share on my network an icon is created on the desktop given me a link to the windows share.

If I try to navigate to the windows share in a terminate for exmaple cd ~/Desktop/windows share the directory is not there.

Also it is not available under /mnt/

How can I find the windows share in my file system? Is this a Samba thing?

---

### Post by cariboo on 2009-05-15
When you mount shares using nautilus, the share is in ~/.gvfs

---

### Post by deanwarren on 2009-05-17
Thanks for your reply. I am using Nautilus as a file manager but my windows share does not appear in ~/.gvfs.

Note I am not manually mounting this drive. It is a USB2 drive and auto mounts.

Any idea where the share is in the file system?

---

