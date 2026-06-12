---
title: "Extract CUE/BIN files"
date: 2006-08-05
forum: Desktop Environments
---

### Post by marcus16 on 2006-08-05
How can I extract CUE/BIN files in Ubuntu? Thanx.

---

### Post by cilynx on 2006-08-05
```

sudo apt-get install bchunk
bchunk <image.bin> <image.cue> <basename>
sudo mount -o loop basename.iso /mnt
sudo ls /mnt

```

Or in English:  
Get binchunker
Use binchunker to make your bin/cue into an iso
Mount the iso
Do whatever

---

