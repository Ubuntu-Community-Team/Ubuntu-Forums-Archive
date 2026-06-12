---
title: "grub doesn't auto load os"
date: 2011-10-22
forum: Desktop Environments
---

### Post by janmyszkier on 2011-10-22
Since I've installed 11.10 I cannot make grub to load default os. It just shows grub menu and stands still. 

Usually it automatically loaded ubuntu after 10 seconds or so. but now i see no counter at all and wating even minutes doesn't boot up the selected os.

please let me know of any files you need.

---

### Post by tom4everitt on 2011-10-22
What does your /etc/default/grub file look like? Either you can just post the content here, or try to read it yourself; in the latter case, this might be useful
[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)
The GRUB_HIDDEN_TIMEOUT and GRUB_TIMEOUT parameters will be of particular interest.

---

