---
title: "New kernel not running"
date: 2021-07-21
forum: Desktop Environments
---

### Post by thumper76 on 2021-07-21
Running Ubuntu 20.04. The automatic updater has downloaded the latest  kernel (5.8.0-63.71) to my machine but for some reason "uname -a" shows  it is still running the older kernel (5.8.0-59.66). How do I force it to  use the latest kernel?

---

### Post by grahammechanical on 2021-07-21
What is the output of?

```
sudo update-grub
```

You should see references to linux image and initrd image for kernel 5.8.0-63 generic listed before kernel 5.8.0-59 generic. Running the update-grub command may correct the situation.

Regards

---

### Post by thumper76 on 2021-07-21
This is what I get --

ricky@BigBopper:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-63-generic
Found initrd image: /boot/initrd.img-5.8.0-63-generic
Found linux image: /boot/vmlinuz-5.8.0-59-generic
Found initrd image: /boot/initrd.img-5.8.0-59-generic
Found Kali GNU/Linux Rolling on /dev/nvme0n1p3
Adding boot menu entry for UEFI Firmware Settings
done

ricky@BigBopper:~$ uname -a
Linux BigBopper 5.8.0-59-generic #66~20.04.1-Ubuntu SMP Thu Jun 17 11:14:10 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by thumper76 on 2021-07-21
OK, problem solved!! I have a dual boot system with Kali-Linux. Running "sudo update-grub" in Kali fixed it for Ubuntu. It seems Kali-Linux has control of grub. Thanks for the help.

---

