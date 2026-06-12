---
title: "What partitioner is included with the alternate-install cd?"
date: 2009-01-19
forum: General Help
---

### Post by stefangr1 on 2009-01-19
I want to make a small pxe rescue os, since I recently experienced that one based on SysRCD isn't working on all machines. I would like to put the same partitioner on it as the one on the alternate-install cd, but I can't find it (I somewhere read it's qtparted, but I know that one uses X). Does anyone know what I have to install?

---

### Post by Titan8990 on 2009-01-19
Not sure what partitioner it uses exactly but qtparted and gparted are both just front-ends for the CLI program: parted.

I would look in to parted.

---

### Post by jerome1232 on 2009-01-19
it's partman, you can install it by installing the obiquity package

```
sudo apt-get install obiquity
sudo partman
```

---

### Post by stefangr1 on 2009-01-19
Thank you very much for the quick response, it was indeed partman with ubiquity.

---

### Post by stefangr1 on 2009-01-20
Unfortunately partman doesn't works, it gives an error that says "no root filesystem". Apart from that, ubiquity was a bit larger than I had expected (71.2mb was installed). So I'll stick with parted, which seems nice.

---

