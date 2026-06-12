---
title: "prevent desktop icons from fstab"
date: 2009-06-20
forum: General Help
---

### Post by bonfire89 on 2009-06-20
Hey there!

How can I prevent the mounts that I do through /etc/fstab from showing up on my desktop?

Automatic mounts such as usb keys should still create a desktop icon.

I'm using Ubuntu 8.04.

Thanks.

---

### Post by michy99 on 2009-06-20
One way to keep partitions from showing up on the desktop is to mount them in /mnt instead of /media.

---

### Post by bonfire89 on 2009-06-20
not sure if this location would have the same effect as /media

```

//server/public/videos /home/myAccount/server-videos cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

---

### Post by bonfire89 on 2009-06-21
a solution is found here

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)


it will hide your flash drives etc. but, they can be access through "computer"


on another not... this gconf-editor thing is pretty cool! I didn't know it existed.

---

