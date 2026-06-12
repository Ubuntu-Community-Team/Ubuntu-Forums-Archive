---
title: "Mounted drives on Desktop - Hardy"
date: 2008-05-02
forum: Desktop Environments
---

### Post by john6six on 2008-05-02
Hopefully this is an easy fix. I mount a network drive in a folder in my home directory. When it mounts, it also places an icon on my desktop. I do not want these showing up here. Is there a way to prevent this from appearing on the desktop?

Here is the line from fstab:
//192.168.1.98/newsrover /home/john/Newsrover cifs credentials=/home/john/.smbcredentials,uid=1000 0 0

Thanks in advance

---

### Post by bmac on 2008-05-03
Open configuration editor.
Select apps/nautilus/desktop/
Check "volumes_visible"

Hope this helps.

---

### Post by bmac on 2008-05-03
Sorry it should read uncheck in the last line

---

### Post by trondhuso on 2008-05-03
Problem with the invisible volumes is that it also hides mounted CD-roms and USB-disks - Which could be handy to have on the desktop.

---

### Post by john6six on 2008-05-03
Thanks, figured it was an easy fix. As far as USB devices and CD/DVD's, they still appear in the places menu. I can live with that. I like a clean desktop, with no icons.

Thanks

---

