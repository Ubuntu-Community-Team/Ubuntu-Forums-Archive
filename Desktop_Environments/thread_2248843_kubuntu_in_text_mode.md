---
title: "kubuntu in text mode"
date: 2014-10-17
forum: Desktop Environments
---

### Post by razvan4 on 2014-10-17
I want Kubuntu 14.04 to start in text mode, how can I stop kdm. I tried this [http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)  but not working.

---

### Post by ajgreeny on 2014-10-17
You can edit **/etc/default/grub** and change the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to read ```
GRUB_CMDLINE_LINUX_DEFAULT="text"
``` then run command **sudo update-grub**.

Did you forget the final command?

---

