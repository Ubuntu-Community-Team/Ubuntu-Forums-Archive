---
title: "Mount Point 0.o"
date: 2009-04-03
forum: General Help
---

### Post by Colo2 on 2009-04-03
I have an iso I am trying to mount with the following command:

> sudo mount -t iso9660 isoimage01.iso mount.point -o loop


But I dont know what to put where it says mount.point :(

PLease help. Thanks

---

### Post by logic++ on 2009-04-03
It expects to define in which folder you want the iso to appear.

For example, if you have a folder on your Desktop named "fld" then the command should be:
```
sudo mount -t iso9660 isoimage01.iso /home/yourusername/Desktop/fld -o loop
```

---

### Post by Colo2 on 2009-04-03
Thats brilliant, thanks for the great help :)
No matter what people say, linux is simpler than Windows once you know how to use it, and you learn every day :p

---

### Post by logic++ on 2009-04-03
Glad you feel that way.

It might not be that simple but there is a reason for that ;)

---

### Post by Colo2 on 2009-04-03
:)

---

