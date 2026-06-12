---
title: "Multiple versions available"
date: 2009-02-04
forum: General Help
---

### Post by matthew.ball on 2009-02-04
Hello,

I downloaded a program called "startupmanager".

In this program, under Default Operating System, there are 3 previous versions of the Linux kernel (as far as I am aware), but it's a single install machine.

Is it possible to remove the previous versions (so I only have the latest one available)?

Could it be *pointlessly* using hard-drive space?
Or are the previous versions just in case something goes wrong?

---

### Post by Neural oD on 2009-02-04
I would not recommend deleting them - they are there in case something goes wrong - and they don't take up that much space

---

### Post by matthew.ball on 2009-02-04
Thanks for the quick reply.

---

### Post by Neural oD on 2009-02-04
no problem - the kernel images are only about 2mb big - so it's really not a prolem -remember that if you're running out of space - make sure that u've emptied the trash!

---

### Post by mcduck on 2009-02-04
They are there in case something goes wrong, but you really don't neeed more than one older version available.

While the kernel image itself is fairly small, together with headers, restricted modules and other related packages they can take quite a lot of disk space. (150–200MB per every kernel version)

You can just uninstall the old versions with Synaptic. Most people keep one older version available, but you could just as well remove even that one after you have confirmed that the latest kernel works fine for you.

---

