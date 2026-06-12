---
title: "Kernel Defaults?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by skattman on 2005-12-16
Hello:

I'm trying to compile a custom kernel, and I was following a guide on this site, excellent work btw, but i unchecked one too many boxes.  The problem is I dont know which one.  I have DMA support now, however, I cant see my FAT32 drive anymore.  Is there some way I can reset the kernel module screen (make xconfig) revert back to the default I had when I installed ubuntu?

---

### Post by kaamos on 2005-12-16
Assuming that your source for the kernel is in /usr/src linux, and you originally installed the ubuntu x86 version:
```
sudo cp config-2.6.12-10-386 /usr/src/linux/.config
```

---

