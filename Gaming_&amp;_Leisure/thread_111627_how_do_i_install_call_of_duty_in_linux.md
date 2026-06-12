---
title: "how do i install call of duty in linux?"
date: 2006-01-02
forum: Gaming &amp; Leisure
---

### Post by madsalty on 2006-01-02
when ever i try to install call of duty with linux in wine i can't because i fails because, I need to put the second disc in and it won't eject the first bocause it says it is busy. how can i get it to install?

---

### Post by TimonVO on 2006-01-02
You need to unmount the cd drive, in a shell, execute this command:
**sudo umount /dev/cdrom**
or whatever your cdrom/dvdrom drive is.

---

### Post by madsalty on 2006-01-03
thanks that helps, however i think mine is cdrom0 so is that what i change it to?

---

### Post by madsalty on 2006-01-03
I tried that however it still says "device is busy"

---

### Post by Norberg on 2006-01-03
test whit the command eject

---

### Post by madsalty on 2006-01-03
That didn't work:
> family@Home:~$ sudo eject /dev/cdrom
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed
family@Home:~$


---

### Post by gil-galad on 2006-01-03
Try [this]("http://liflg.org/?catid=7&gameid=1") installer.  It will ask you for your cds and set it up for you to use with wine.

---

