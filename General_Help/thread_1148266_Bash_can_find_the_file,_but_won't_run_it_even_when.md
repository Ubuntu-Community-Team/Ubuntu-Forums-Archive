---
title: "Bash can find the file, but won't run it even when execution is permitted"
date: 2009-05-04
forum: General Help
---

### Post by samjh on 2009-05-04
This is very very weird.

I have the ETQW installer (ETQW-client-1.5-full.x86.run) in my ~/temp/install directory.  I'm trying to run it, but it just won't run.

```
~/temp/install$ ./ETQW-client-1.5-full.x86.run
bash: ./ETQW-client-1.5-full.x86.run: No such file or directory
```

If I try ./ETQW*.run, it still says:
```
./ETQW*run
bash: ./ETQW-client-1.5-full.x86.run: No such file or directory
```

I've checked the file permissions, and it has executable permission.  The file is obviously there.  Bash can find the file when I use the * wildcard, but I can't understand why it says it doesn't exist! :confused:

---

### Post by Bakker on 2009-05-04
Try:
```
chmod +x ./ETQW-client-1.5-full.x86.run
```
```
sh ./ETQW-client-1.5-full.x86.run
```

---

