---
title: "Hide Boot Up Text"
date: 2006-07-14
forum: Desktop Environments
---

### Post by vtec on 2006-07-14
I'm trying to make a kiosk type system. I would like to hide as much boot up text as possible. I would be very happy if the system came up and only displayed one message, for example "The system is now starting up...", untill  gnome loaded. Is this possible??

---

### Post by ciscosurfer on 2006-07-14
You can edit your **/boot/grub/menul.lst** file and get rid of any options on your kernel line *after* the word **splash** (i.e., getting rid of any **vga=xxx** options).  This will disable all text text from flying by.  As for a boot-up text, I'll need to research this.  But it seems like it can be done.

---

