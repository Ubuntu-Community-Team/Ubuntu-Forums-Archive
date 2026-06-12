---
title: "Acetoneiso2 mount help"
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by campkillgemma on 2007-11-11
Can someone please help me ive been tring this all day.... when I try to mount a .iso image in acetoneiso2 a dialog pops up and says


"Process Error Code: 1"


Would someone be able to help me? Thanks :)

---

### Post by Sockerdrickan on 2007-11-11
mount -o loop -t iso9660 file.iso /mnt/test

just do it like that =)

---

### Post by bulletxt on 2007-11-11
are you running latest 1.96 version?
did you activate fuse? :

   open a terminal and as root user type:

   chmod 4755 /usr/bin/fusermount  (may be /bin/fusermount depending on distro)
   chmod o+rw /dev/fuse
   addgroup <your-user> fuse  (ex. addgroup johndoe fuse)

---

