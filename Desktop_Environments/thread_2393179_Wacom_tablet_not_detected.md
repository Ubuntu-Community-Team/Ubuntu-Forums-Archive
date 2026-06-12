---
title: "Wacom tablet not detected"
date: 2018-05-30
forum: Desktop Environments
---

### Post by wykke on 2018-05-30
Hello, this is my first week on linux, i'm really enjoying but i'm  having issues with my wacom tablet. There's a lot of topic about it, i  tried many things but isn't working. The tablet is working on windows 10, and i tried to use on ubuntu, zorin and manjaro.

```

$ uname -r
4.15.0-22-generic

```

```

$ lsusb | grep Wacom
Bus 001 Device 006: ID 056a:037a Wacom Co., Ltd 

```

```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB OPTICAL MOUSE                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Synaptics TM3336-001                        id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; EasyCamera: EasyCamera                      id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

```

$ xsetwacom --list devices

```
(returns nothing)

```

$ lsmod | grep wacom
wacom                 106496  0
usbhid                 49152  1 wacom
hid                   118784  5 i2c_hid,hid_generic,usbhid,hid_rmi,wacom

```

```

$ apt list libwacom2
Listing... Pronto
libwacom2/bionic,now 0.29-1 amd64 [installed]

$ apt list libwacom-common
Listing... Pronto
libwacom-common/bionic,bionic,now 0.29-1 all [installed]

$ apt list xserver-xorg-input-wacom
Listing... Pronto
xserver-xorg-input-wacom/bionic,now 1:0.36.1-0ubuntu1 amd64 [installed]

```

---

### Post by jamautry on 2018-10-25
I am having the same exact issue.  Is anyone willing to pass on some advice?  Thanks in advance.

---

### Post by wildmanne39 on 2018-10-25
Hello and welcome to the forum jamautry, please start your own thread so you can get the help you deserve instead of posting in someone else's thread.

Thanks

---

### Post by jamautry on 2018-10-25
I posted in this thread because I am having the exact same problem as this person and the OP posted this back in May so I thought I would give it a bump.

---

### Post by lokoyote on 2018-12-03
Hi!

I had the same problem, the only thing who worked for me was to install the latest kernel with **Ukuu** ([https://doc.ubuntu-fr.org/ubuntu_kernel_upgrade_utility](https://doc.ubuntu-fr.org/ubuntu_kernel_upgrade_utility)).
In Ubuntu 18.04 the default kernel is the 4.15 version. So I upgraded to the latest stable version 4.19.6 with success, and after a reboot, the tablet is recognized.

Hope this will help!

---

