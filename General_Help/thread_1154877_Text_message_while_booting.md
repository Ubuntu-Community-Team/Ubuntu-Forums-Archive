---
title: "Text message while booting"
date: 2009-05-10
forum: General Help
---

### Post by mosaic2s on 2009-05-10
while booting - before the ubuntu logo comes - the screen says some message - like firmware error # 28232. pl inform ubuntu maintainers and bios vendor.

How can I copy or locate this text?

---

### Post by vahnx on 2009-05-10
Check out [http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/](http://www.foogazi.com/2008/06/07/quickzi-how-to-log-boot-messages-in-ubuntu/)

You change /etc/default/bootlogd 
BOOTLOGD_ENABLE=No
to
BOOTLOGD_ENABLE=Yes

Then you can view logs in /var/log/boot

---

### Post by mosaic2s on 2009-05-10
THANKS.
have done the editing of the file.
Yet to test the waters. will report.

---

