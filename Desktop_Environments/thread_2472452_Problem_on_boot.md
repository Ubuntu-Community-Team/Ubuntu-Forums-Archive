---
title: "Problem on boot"
date: 2022-02-27
forum: Desktop Environments
---

### Post by zuzzuz-2000 on 2022-02-27
Hello, i have an ubuntu 20.04 on my pc, it worked good until i try to follow this guide:
[HTML]https://stopanddecrypt.medium.com/a-complete-beginners-guide-to-installing-a-bitcoin-full-node-on-linux-2021-edition-46bf20fbe8ff#8ca1[/HTML]
I used ```
sudo checkinstall
``` instead of ```
sudo make install
```
After that i can't boot cause that error:
```
[COLOR=#101010][FONT=Ubuntu]Kernel panic on boot: run-init: /sbin/init: No such file or directory.[/FONT][/COLOR]
```
I tried to follow this thread
[HTML]https://askubuntu.com/questions/833735/kernel-panic-on-boot-run-init-sbin-init-no-such-file-or-directory[/HTML]
but when i try to use ```
[COLOR=#005400][FONT=Monaco]sudo chroot /mnt[/FONT][/COLOR]
``` i have this error ```
[COLOR=#101010][FONT=Ubuntu]chroot: failed to run command '/bin/bash': No such file or directory.[/FONT][/COLOR]
```
Someone can help me?
Thanks.

---

### Post by zuzzuz-2000 on 2022-02-28
Solved with [HTML]https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/1847582[/HTML]

---

