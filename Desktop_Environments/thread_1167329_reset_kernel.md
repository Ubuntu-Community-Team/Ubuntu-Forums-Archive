---
title: "reset kernel"
date: 2009-05-22
forum: Desktop Environments
---

### Post by noelc on 2009-05-22
Hi,

I am new  to linux and keen to learn.  I Run Virtual Box 2.2.2 with XP installed . My desk top environment O/S is Ubuntu 8.10

Not sure why but I can no longer start my virtual box and get a message saying I need to reset the kernel module by executing 

'/etc/init.d/vboxdrv setup'

I have assumed that I need to type this into the terminal and press enter but when I do this I get  "No such file or directory".

Would appreciate some help

Thanks

---

### Post by GOfree on 2009-05-22
Did you run the command in superuser mode?

Try "sudo /etc/init.d/vboxdrv setup".

---

### Post by noelc on 2009-05-23
GOfree thankyou thankyou thankyou.

Works a treat

---

