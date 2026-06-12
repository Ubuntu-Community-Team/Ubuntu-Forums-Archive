---
title: "deamon tools?"
date: 2005-12-08
forum: General Help
---

### Post by m3ck4rn on 2005-12-08
hello!
I would like to have something like deamon tools for ubuntu.
so i can burn dvd images and whatch on my laptop without have to burn a real dvd record everytime.

is there something like that for me that I can apt-get in to ubuntu?

---

### Post by RAOF on 2005-12-08
Actually, yes.  It's the "loopback" device:

```
sudo mount -o loop /path/to/image.iso /mnt/imagemount
``` will mount the iso image in the /mnt/imagemount directory (which needs to exist first).

EDIT: This is only for nice, simple .iso files.  If you've got stuff in a wierd, proprietry format (like .b5t like blindread makes, or whatever) it's unlikely to work.

---

### Post by kaamos on 2005-12-08
The above works also at least with .img-files in addition to .iso. If you have .bin images you can convert them to iso with bchunk.

---

### Post by jliedeka on 2005-12-08
You might have to add a -t flag.  Traditionally I always added -t iso9660 for CD images.  I think DVD images also share that filesystem type.

---

### Post by MetalMusicAddict on 2005-12-08
I wounder if s little GUI tool could be written to do this?

---

