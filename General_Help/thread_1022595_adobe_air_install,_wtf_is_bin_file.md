---
title: "adobe air install, wtf is bin file?"
date: 2008-12-27
forum: General Help
---

### Post by SonnHalter on 2008-12-27
tried to install adobe air but they gave me a .bin file what do i do with it?

---

### Post by lykwydchykyn on 2008-12-27
give it execute permissions, then run it.  Probably with sudo.

---

### Post by SonnHalter on 2008-12-27
thx. gave it permission and then dragged to terminal

---

### Post by lykwydchykyn on 2008-12-27
```

cd directory_where_you_put_the_file
sudo ./file_you_downloaded.bin

```

---

### Post by namdung on 2008-12-27
> **SonnHalter said:**
> tried to install adobe air but they gave me a .bin file what do i do with it?

First go to the folder with the .bin file
Make the file executable
```
sudo chmod +x filename
```

Install the file
```
sudo ./filename
```

---

### Post by jerome1232 on 2008-12-27
Basically they are the equivelant to a Windows .exe file, they are just executable **bin**ary files.

They don't always have an extension and I've seen .run .bin .sh. Just know for now on that when you download binary files you just give them executable permission and double-click them to run them.

---

### Post by lykwydchykyn on 2008-12-27
Just a hint, the "file" command will usually give you some indication of what a given file is.  e.g.:
```

# file /bin/bash
/bin/bash: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

```

---

