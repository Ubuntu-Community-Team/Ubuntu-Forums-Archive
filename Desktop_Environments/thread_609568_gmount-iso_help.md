---
title: "gmount-iso help"
date: 2007-11-11
forum: Desktop Environments
---

### Post by campkillgemma on 2007-11-11
im trying to install American McGee's Alice it has two disk images. When gmount asks for the second disk im not able to unmount the first disk image and put on the second one.

Is there any other way to do this? Make make a virtual drive or something? because when i mount it to cdrom0 it mounts to cdrom as well.

Anyone got any ideas?

---

### Post by atomkarinca on 2007-11-11
you can try [acetoneiso2]("http://www.acetoneteam.org/central.html"), it supports more types and you can mount multiple image files.

---

### Post by campkillgemma on 2007-11-11
when i try and mount i get a dialogbox that says "process error code 01"

---

### Post by bulletxt on 2007-11-11
did you activate fuse?

 open a terminal and as root user type:

   chmod 4755 /usr/bin/fusermount  (may be /bin/fusermount depending on distro)
   chmod o+rw /dev/fuse
   addgroup <your-user> fuse  (ex. addgroup johndoe fuse)


if still getting problems on mount, then convert the image allways with AcetoneISO2. you'll find the option in the gui.

---

