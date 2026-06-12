---
title: "Problems installing ubuntu on a new primary partition"
date: 2009-04-22
forum: General Help
---

### Post by lurikeen on 2009-04-22
I'm trying to install ubuntu on my 3rd primary partition of my 640 GB drive. I formatted it as ntfs, which I know won't work, but when I select the partition (in the manual section of the partitioner) and attempt to format it tells me I need to go to the partition preferences menu. I don't know what to do about this... also, what filesystem should I use?

Thanks.

---

### Post by Merk42 on 2009-04-22
EXT3, if you're trying Jaunty, you can try EXT4, but EXT3  is a safe bet.

---

### Post by codeseer on 2009-04-22
Try removing it, then creating it new as Ext3.

---

### Post by lurikeen on 2009-04-23
Thanks guys. Thats what I needed to do.

---

