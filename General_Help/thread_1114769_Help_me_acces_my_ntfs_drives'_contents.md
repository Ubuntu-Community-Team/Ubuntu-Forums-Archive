---
title: "Help me acces my ntfs drives' contents"
date: 2009-04-03
forum: General Help
---

### Post by pedramslhr on 2009-04-03
Hi
I have a dell vostro 1510 with Win vista home basic and ubuntu.
Windows Vista has failed to boot and I'm going to recover my laptop, So all of my files will be removed.

Problem is that I cant access my ntfs drives to access my files via ubuntu before recovering my windows.

Following message is displayed when opening ntfs drive.
And after some seconds the next one

---

### Post by davec64 on 2009-04-03
If you look at your first screenshot there's a command there that forces mounting of your NTFS partition. 


```
mount -t ntfs-3g /dev/sda3 /media/OS -o force
```

Type this in at a terminal and all should be ok!

---

### Post by pedramslhr on 2009-04-03
> **davec64 said:**
> If you look at your first screenshot there's a command there that forces mounting of your NTFS partition. 




Type this in at a terminal and all should be ok!

And it will not damage my files? It's so important for me.

---

### Post by azmo35 on 2009-04-03
Hi,from the first screenshot you can tray force it to mout but maybe dosen't work, so go to applications/accessories/terminal and type
mout -t ntfs-3g/dev/sda3/media/OS -o force 
and see if you can access it.

---

### Post by pedramslhr on 2009-04-03
Thanks guys!
It worked correctly

---

