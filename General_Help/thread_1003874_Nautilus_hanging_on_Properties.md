---
title: "Nautilus hanging on Properties"
date: 2008-12-06
forum: General Help
---

### Post by cong06 on 2008-12-06
Whenever I right click on an mkv file to try and change the program it opens with it hangs on properties.

is there a way to fix it? or a work around even?

---

### Post by cong06 on 2008-12-06
A reply from [drs305](http://ubuntuforums.org/member.php?u=223945) showed me a link:
[http://ubuntuforums.org/showthread.php?t=51012](http://ubuntuforums.org/showthread.php?t=51012)

which pointed me towards the file:
/usr/share/applications/defaults.list

Which was what I needed.
Simply replaced all "totem" with "vlc" and now it's doing exactly what I wanted.

---

