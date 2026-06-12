---
title: "cant delete a folder on my desktop"
date: 2006-06-23
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-06-23
I have a folder called "loopmnt" on my desktop, icant delete it. Ubuntu tells me its read only, i cant save anything over it, and i cant delete it, even with 
sudo rm -rf

i get an errror sayign 
rm: cannot remove `/home/crowell/Desktop/loopmnt/firmware.bin': Read-only file system

---

### Post by nix4me on 2006-06-23
Sounds like its a mount point.  Do you have an umount option if you right click it?

nix4me

---

### Post by Winblowz on 2006-06-23
Have you tried using Nautilus as root and then deleting it? If you're using KDE, then try launching Konqueror as root and deleting it.

---

### Post by aysiu on 2006-06-23
Can you post the output of this command? ```
df -h
```

---

### Post by %hMa@?b&lt;C on 2006-06-23
it was a mount point, problem solved

---

