---
title: "how to use same file in windows and ubuntu?"
date: 2010-07-19
forum: Desktop Environments
---

### Post by rizos on 2010-07-19
i install rosseta stone on the windows partition and also on ubunutu with wine.


but i would like to use the language packages installed on windows on ubuntu as well.


is there a way to set a route to the language package installed on windows so ubuntu will use the same file, that way i just intsall it only one time.


thanx.

---

### Post by masebase on 2010-07-19
Ubuntu 10.04 shows me my window drive under the Places menu as a Filesystem with x Gb  of space. Once I click on it Ubuntu auto mounts it. I can then see it under /media. At this point you could make a symbolic link to it.

ln -s /your/file /your/link

 This is all a hack. I know you can modify your /etc/fstab file to have it mount all the time.

That would be a start. Don't know if it is a good idea. :)

---

