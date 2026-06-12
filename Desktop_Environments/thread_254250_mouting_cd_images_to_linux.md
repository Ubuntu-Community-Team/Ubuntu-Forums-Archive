---
title: "mouting cd images to linux"
date: 2006-09-09
forum: Desktop Environments
---

### Post by rabid9797 on 2006-09-09
like alcohol 120 and daemon tools does. does anybody know of any programs that can do this?

---

### Post by taurus on 2006-09-09
```

sudo mkdir /mnt/iso
sudo mount -i iso9660 -o loop <filename>.iso /mnt/iso

```
That's (the second command) how you mount an ISO file in Linux...

---

### Post by rabid9797 on 2006-09-09
thanks :D

---

### Post by jstroot on 2006-09-09
That second command didn't work for me. It kicks out a usage statement.

Any ideas?

---

### Post by galv on 2006-09-12
Can you tell which usage statement?

---

### Post by mitch.c on 2006-09-12
The '-i' in the previous example is incorrect I believe. Try this (assumes /mnt/iso exists):
```
sudo mount -t iso9660 -o loop /path/to/file.iso /mnt/iso
```

---

