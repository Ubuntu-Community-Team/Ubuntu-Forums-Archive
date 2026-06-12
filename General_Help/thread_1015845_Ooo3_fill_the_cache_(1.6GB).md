---
title: "Ooo3 fill the cache (1.6GB)"
date: 2008-12-19
forum: General Help
---

### Post by Makaai on 2008-12-19
After launching Ooo3 (installed from official Ooo3 debs) and also after closing it, this is the output of free -m:

```
luca@daneel810:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3545       1690       1854          0        136       1062
-/+ buffers/cache:        490       3054
Swap:         3812          0       3812
```

I've found in this forum this workaround to flush cache

```
sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches"
```

but this is not a solution: I can't launch that command everytime I close Ooo3! Is there any solution?

I have also some problem of visualization in Ooo3, sometimes some buttons disappear when I'm moving around the menu.

---

### Post by sdennie on 2008-12-19
Why do you want to flush the cache?  Having the cache grow to fill all available free memory is a very, very good thing for the performance of the machine.

---

### Post by Makaai on 2008-12-19
Maybe I was wrong choosing my english words (I'm italian).
I meant: I want to empty the cache! Is it a bad thing about the 30% of cache memory full, or I'm wrong?

---

### Post by sdennie on 2008-12-19
No, it's a very good thing that the cache is growing large.  To see what the cache does, open Ooo3 Writer and time how long it takes.  Now close it, drop the cache and see how long it takes to open.  Now close it and without dropping the cache, see how long it takes to open.  You should notice it opens much faster when the caches aren't dropped.

---

### Post by Makaai on 2008-12-19
Your're right, is it and Ive saw it, but I'm worried about a possible slowing down of computer performances...So there will be any problem?

---

### Post by sdennie on 2008-12-19
It's natural for the cache to grow to fill all free memory.  If your applications need that memory, the kernel will drop memory from the cache to make room for your applications so, there is no performance disadvantages for letting the cache grow.

---

