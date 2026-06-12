---
title: "understanding memory usage"
date: 2009-01-09
forum: General Help
---

### Post by pablop on 2009-01-09
Hi,

I'm using 'free' to see memory usage on my ubuntu server 8.10.
Can you please explain the difference between Mem and buffers/cache?
I expect low memory usage but there is almost no free Mem. On the other hand there is a lot of free buffers/cache.

             total       used       free     shared 
Mem:       1747764    1601008     146756          0
-/+ buffers/cache:      91864    1655900
Swap:       917496        496     917000

Thanks

---

### Post by lloyd_b on 2009-01-10
> **pablop said:**
> Hi,

I'm using 'free' to see memory usage on my ubuntu server 8.10.
Can you please explain the difference between Mem and buffers/cache?
I expect low memory usage but there is almost no free Mem. On the other hand there is a lot of free buffers/cache.

             total       used       free     shared 
Mem:       1747764    1601008     146756          0
-/+ buffers/cache:      91864    1655900
Swap:       917496        496     917000

Thanks

You're misunderstanding what the "-/+ buffers/cache" line means.

The "Mem:" line is shows what memory is in use.  Since Linux will by default attempt to use any free memory for buffering/caching, this will almost always show very little free.

The "-/+ buffers/cache:" line tells you what memory is in use, *excluding* memory being used by buffers or cache.

So in the above example, you have 1747764 total memory, with 1601008 being used.  But once you take the buffers/cache out of the picture, you're actually only using 91864, with 1655900 free.

If/when a program needs more memory, Linux will quietly reduce the size of the buffer/cache area, and give that memory to the requesting program.

In summary - you have plenty of free memory on that machine...

---

### Post by cdtech on 2009-01-10
> **pablop said:**
> Hi,

I'm using 'free' to see memory usage on my ubuntu server 8.10.
Can you please explain the difference between Mem and buffers/cache?
I expect low memory usage but there is almost no free Mem. On the other hand there is a lot of free buffers/cache.

             total       used       free     shared 
Mem:       1747764    1601008     146756          0
-/+ buffers/cache:      91864    1655900
Swap:       917496        496     917000

Thanks

Here is some information that may be helpful:
[http://tldp.org/LDP/sag/html/buffer-cache.html](http://tldp.org/LDP/sag/html/buffer-cache.html)

---

