---
title: "open bin files"
date: 2006-01-29
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-01-29
So i downloaded a .BIN file, but how do I open it?

---

### Post by Gcool on 2006-01-29
Try the following:

* chmod +x filename.bin
* ./filename.bin

---

### Post by Juergen on 2006-01-29
Probably installs something system-wide, so you might need
```
sudo ./filename.bin
```

---

### Post by stiankarlsen on 2006-01-30
wont work.

anything else?

---

### Post by f1dave on 2006-01-30
in a terminal, do an ls -a on the file

give us the output, which shows the permissions for the file, and we might be able to suggest something.

---

### Post by stiankarlsen on 2006-01-30
figured it out


used bchunk to convert it to an ISO, and just took it from there. but thanks guys

---

