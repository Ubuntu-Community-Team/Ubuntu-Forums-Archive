---
title: "Parted with special alignment"
date: 2009-05-15
forum: General Help
---

### Post by lfaraone on 2009-05-15
Hi,

I need to create a few partitions aligned on 4MB blocks by using 32 sectors/track and 128 heads and using odd start numbers. Is it possible to do this with parted, and if so, how?

I'm trying to create a disk that is USB_ZIP compatible, and it needs to meet those specs.

---

### Post by Intrepid Ibex on 2009-05-15
What? 4mb partitions?

---

### Post by lfaraone on 2009-05-15
> **Intrepid Ibex said:**
> What? 4mb partitions?
 
No, partitions of various sizes that use a block size of 4mb.

---

### Post by Intrepid Ibex on 2009-05-16
Oh right, well [google]("http://justfuckinggoogleit.com") ( **x)** ) is your friend: [link]("http://www.google.com/search?q=change+block+size&btnG=Search") ^^

---

### Post by lfaraone on 2009-05-16
> **Intrepid Ibex said:**
> Oh right, well [google]("http://justfuckinggoogleit.com") ( **x)** ) is your friend: [link]("http://www.google.com/search?q=change+block+size&btnG=Search") ^^
I know how to change the block size with a tool such as *fdisk*, however I don't know how to do so using *parted*, which (AFAICT) cannot work with disks that use alternate block sizes. And I have a task that needs parted.

---

