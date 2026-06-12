---
title: "File system using aufs on usb flash drive"
date: 2009-04-21
forum: General Help
---

### Post by dstempfley on 2009-04-21
I'm setting up encrypted file systems on a flash disk using aufs and dm-crypt.  I want to protect the flash disk from too many writes.  My gut says to use ext2 as the base file system since ext3 journaling would increase the number of writes. The other thought is that ext3 is more resilient and could handle an occasional unsafe device removal.  I've seen examples that use both, and little discussion on why.  

Is there a more correct solution?

/Dion

---

### Post by Menschenfresser on 2009-04-22
I have heard (a couple of times) that newer usb sticks are not affected much by writes since they use internally a levelling algorithm. Not sure what to think about it and whether it really means we can use journaling. On my stick I have just used ext3 (data is more important and it is not likely that I won't lose the usb stick in the next years...)

---

### Post by dstempfley on 2009-04-22
Good thoughts.

Thanks,

/Dion

---

