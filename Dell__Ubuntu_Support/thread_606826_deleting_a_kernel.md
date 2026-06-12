---
title: "deleting a kernel"
date: 2007-11-08
forum: Dell  Ubuntu Support
---

### Post by DouglasAWh on 2007-11-08
I've recently be chastised for posting in old threads, so even though there is a thread by the same title, I'm reposting.

How do I delete an old kernel?  I tried just changing the default kernel but the instructions I got here did not work.

Thanks.

---

### Post by patriciajh on 2007-11-10
Just uninstall it using your preferred package manager.
For instance:

sudo aptitude remove linux-image-2.6.xx-xx-generic

(changing 2.6.xx-xx-generic to your kernel numbers)

or in synaptic search on "linux-image", right-click the one you want to delete, and choose "remove" 

BUT MAKE SURE you have another kernel on your system WHICH YOU HAVE ALREADY BOOTED WITH SUCCESSFULLY, before you do this.

HTH.

---

### Post by DouglasAWh on 2007-11-10
I ended up just changing my default kernel, but thanks!

---

