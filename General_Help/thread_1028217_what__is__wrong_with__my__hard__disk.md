---
title: "what  is  wrong with  my  hard  disk??"
date: 2009-01-02
forum: General Help
---

### Post by luofeiyu on 2009-01-02
sudo badblocks -s -v /dev/sdb7


done
Pass completed, 18156760 bad blocks found.

i've  checked  out  for  3  times  ,so  many   bad blocks??
can i  belive  in  it?

---

### Post by Tomatz on 2009-01-02
> **luofeiyu said:**
> sudo badblocks -s -v /dev/sdb7


done
Pass completed, 18156760 bad blocks found.

i've  checked  out  for  3  times  ,so  many   bad blocks??
can i  belive  in  it?

Sounds like its damaged. You could try a low level format but this will **ERASE THE ENTIRE DISK** not just the partition. I had the same happen to me and i ended up having to low level format. If it is just a storage partition you could just take it out of /etc/fstab and forget about it until a later date but if you keep mounting it you could start to damage the other partitions (weird i know).

---

### Post by sefs on 2009-01-02
Spinrite ([http://grc.com](http://grc.com)) that thang!

---

