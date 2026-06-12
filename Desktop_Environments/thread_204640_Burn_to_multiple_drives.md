---
title: "Burn to multiple drives"
date: 2006-06-27
forum: Desktop Environments
---

### Post by auspuff on 2006-06-27
doen anyone know of any software that can burn to multiple burners? i have tried rdrbq, cdxroast and cdcontrol but no luck so far.

btw i,m new to ubuntu and i,m loving it so far ;-)

---

### Post by b0bby on 2006-06-27
same data to several burners?
cdrecord dev=/dev/cdrom1 & cdrecord dev=/dev/cdrom2 & cdrecord dev=/dev/cdrom3 sould do the trick

(ofcourse, u need to change the commandline abit to fit your needs =)

---

### Post by Ramses de Norre on 2006-06-27
Wont that command burn the data to one drive a time? I think the topic starter would like all the drives burning at the same time.

---

### Post by auspuff on 2006-06-27
yes preferably to multiple devices at once

cdrecord filename.iso dev=/dev/cdrom1

does not work only:

cdrecord dev=/dev/cdrom

works, do i have to manually mount the drives?

---

