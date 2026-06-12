---
title: "Wine 0.9.22 giving you mcop trouble? try this!"
date: 2006-10-02
forum: Desktop Environments
---

### Post by nu2this on 2006-10-02
If you have just updated wine & you click tthe audio tab then wine crashes. You read terminal& see  cant find mcop or some such thing?
Then rename usr/lib/wine/winearts.drv.so to usr/lib/wine/winearts1.drv.so problem solved!

---

### Post by joshgtv6 on 2006-10-22
ok, what is the command from the terminal to rename a file and the syntax to rename this file.  Also, it appears that you need /root access or else i would just do it from the file manager but the rename option is grayed out.  thanks.

---

### Post by livinginx on 2006-10-31
sudo /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts1.drv.so

---

### Post by mico on 2006-10-31
livinginx meant:

sudo **mv** /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts1.drv.so

---

### Post by livinginx on 2006-10-31
Yes, yes I did.  Thanks LoL.

---

### Post by sbassett on 2006-11-13
Awesome work, nu2this, and just in case anyone is looking for a solution to:

can't create mcop directory

error, this is it. Again, kudos to you.

---

