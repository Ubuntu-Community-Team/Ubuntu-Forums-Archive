---
title: "Wubi - moving disk to other partition on Windows."
date: 2009-04-24
forum: General Help
---

### Post by tom4444444tom on 2009-04-24
Hi! I'm new :)

Now, my problem. I have to format my D:/ partition, but I have there a Wubi with Ubuntu disk. So, how can I move this disk without any crashes? Is there any way to do this?


Regards, Tom. :)

---

### Post by cariboo on 2009-04-24
If you move the Ubuntu partition to a different disk, you will also have to reinstall grub. To move the Ubuntu install to a different partition, use the LiveCD and just copy all the data from the old partition to the new partition. Then once you are finished, use [thread=224351]this[/thread] howto, to repair grub.

---

