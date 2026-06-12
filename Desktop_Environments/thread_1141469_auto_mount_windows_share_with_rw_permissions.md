---
title: "auto mount windows share with r/w permissions"
date: 2009-04-28
forum: Desktop Environments
---

### Post by twistedtwig on 2009-04-28
Hi all,

I have a windows share (unprotected), within my local network.  I added this line to the end of my fstab file

//betty/media /media/bettymedia cifs rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

sudo mount -a works and it mounts the directory.  Files that have r/w permission are great but if I put a new file up there I only have read permission and can not edit or overwrite the file.

How can I fix this please?

Thank you

---

### Post by twistedtwig on 2009-04-30
does anyone have any ideas about this please?

Thanks

---

