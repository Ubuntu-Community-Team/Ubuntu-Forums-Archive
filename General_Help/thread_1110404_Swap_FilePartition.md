---
title: "Swap File/Partition"
date: 2009-03-29
forum: General Help
---

### Post by Lazy8s on 2009-03-29
I found the Swap FAQ but I am looking for a more detailed document explaining the swap file/partition in Ubuntu 8x. I know what it is, how to make and mount it. I am looking for some more technical details such as how it is allocated and where it is stored in the directory structure, etc. I am not sure this is the forum to post in but I couldn't find a "Memory discussion" forum or anything. Any help would be greatly appreciated. Thank you in advance.

---

### Post by Iandefor on 2009-03-29
Not quite certain what you're asking. If you're wondering where it mounts in the filesystem hierarchy... it doesn't because that's not how it's structured. It's just a space on-disk for the kernel to keep [memory pages]("http://en.wikipedia.org/wiki/Paging") when they're not needed.

---

