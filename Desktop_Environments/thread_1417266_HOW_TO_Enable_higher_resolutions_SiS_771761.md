---
title: "HOW TO: Enable higher resolutions SiS 771/761"
date: 2010-02-27
forum: Desktop Environments
---

### Post by st0nes on 2010-02-27
After struggling with this for 2 days and getting nowhere, I found this simple solution.

1. Download packages [http://ajoliveira.com/ajoliveira/gen/bin/sis_driver_32-bit_9.10.tar.gz](http://ajoliveira.com/ajoliveira/gen/bin/sis_driver_32-bit_9.10.tar.gz) and [http://ajoliveira.com/ajoliveira/gen/bin/xorg.conf.tar.gz](http://ajoliveira.com/ajoliveira/gen/bin/xorg.conf.tar.gz).

One of these contains the driver files and the other a xorg.conf file.

2. Extract the 2 archives by double-clicking on them.

3. Copy the xorg.conf file to the /etc/X11 directory:
```
sudo cp xorg.conf /etc/X11
```
4. Go to the directory containing the extracted driver files and copy them to /usr/lib/xorg/modules/drivers:
```
sudo cp * /usr/lib/xorg/modules/drivers
```
5. Reboot.

You will not be able to enable Compiz effects because this is a 2d driver, but it's better than the pig-ugly shambles it was before.

---

### Post by daziplqa on 2010-05-05
Hi bro,

Actually this doesn't work for me,
```

$ uname -a
Linux compu10 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
$ cat /etc/issue
Ubuntu 10.04 LTS \n \l
$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

can you help?

---

### Post by mhgsys on 2010-05-12
To get the sis 771 671 running in ubuntu 10.04 have a look at my "guide"
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

If you are using asus x5dc / k50c follow #438 on [http://ubuntuforums.org/showthread.php?t=958967&page=44](http://ubuntuforums.org/showthread.php?t=958967&page=44)

---

