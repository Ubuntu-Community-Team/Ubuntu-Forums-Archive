---
title: "USB storage device denying permission on 2 partitions"
date: 2009-06-02
forum: General Help
---

### Post by texas.chef94 on 2009-06-02
sdb1-2-3 are storage partitions. They all 3 appear in nautilus as media/disk
media/disk2 and media/disk-3.
Presently I am using media/disk but am denied permission on other 2.
to the best of my memory I used sudo chmond 777 for permission before.
However now I get 
allen@allen-desktop:~$ sudo chmod 777 /media/disk-2
[sudo] password for allen: 
chmod: cannot access `/media/disk-2': No such file or directory
allen@allen-desktop:~$ 
So I assume I need to create a directory to meet my label ID or what?
Please advise in full whatever I must do. Thank you so much

---

