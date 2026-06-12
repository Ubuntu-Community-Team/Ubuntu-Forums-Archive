---
title: "Computer name and workgroup"
date: 2009-02-11
forum: General Help
---

### Post by prc320 on 2009-02-11
Hi

I know I have upgrading to 8.10 but I can't find where to change the computer name and workgroup.
Help



Robert

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by Peter09 on 2009-02-11
you need to edit /etc/hostname for the computer name
and
/etc/samba/smb.conf for the workgroup

---

### Post by prc320 on 2009-02-11
Ok

what happens it I want to do it via GUI?

Robert

---

### Post by Peter09 on 2009-02-11
use the gedit editor but as you need to be superuser you will need to go into a terminal and type

```
gksudo gedit
```

this will open up a GUI editor.

---

### Post by prc320 on 2009-02-11
Ok I will try that.

---

