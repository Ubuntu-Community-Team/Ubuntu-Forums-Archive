---
title: "Ubuntu 10.04 help"
date: 2010-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maxwhell on 2010-10-01
I created a partition with Ubuntu 9.04 and recently installed 10.04 on my C drive alongside windows. But for some reason, it will not allow me to get to it. When I select "ubuntu" it just brings me back to the old 9.04 version. When I explore my C drive in Windows, it has Ubuntu files. I have no idea what to do.

---

### Post by mörgæs on 2010-10-02
Hi, welcome to the forum.

If I understand correctly, you have a working 9.04 (which is running out of support at the end of the month), a defect 10.04 and a working Windows, right?

I would:

Back up all user files in Ubuntu 
Boot a live CD and open Gparted
Delete all Ubuntu partitions, leaving Windows as the only system
Install 10.04 on the newly created space, next to Windows.

---

