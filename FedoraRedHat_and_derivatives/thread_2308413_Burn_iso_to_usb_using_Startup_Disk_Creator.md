---
title: "Burn iso to usb using Startup Disk Creator"
date: 2016-01-02
forum: Fedora/RedHat and derivatives
---

### Post by pjmlmas on 2016-01-02
I have Fedora 21 Fedora-Live-Workstation-x86_64-23-10.iso
I have Ubuntu 12
I have 2 gb formatted fat 32
I open Startup Disk Creator
I select Fedora image, remains grayed out
I select Ubuntu image, ok.

Is this only for Ubuntu images.
I have tried other methods on Fedora site- no go.

Any insight, links, help, appriciated

---

### Post by ubfan1 on 2016-01-02
I'm happy when Startup Disk Creator can use the next release Ubuntu iso -- it's pretty sensitive.
See [http://ubuntuforums.org/showthread.php?t=2291946&highlight=startup+disk+creator](http://ubuntuforums.org/showthread.php?t=2291946&highlight=startup+disk+creator)

---

### Post by Dennis N on 2016-01-02
Ubuntu Startup Disk Creator is only for Ubuntu family distros.
For Fedora, use the direct write methods they suggest at: 
[https://fedoraproject.org/wiki/How_to_create_and_use_Live_USB](https://fedoraproject.org/wiki/How_to_create_and_use_Live_USB) 
You can use Gnome Disk Utility (a.k.a. "Disks") to do the Fedora job. See the "Linux (GNOME) quick start (direct write)" section at above link.
Ubuntu can be done this way too.
Also for Ubuntu: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sammiev on 2016-01-02
+1 for [mkusb]("https://help.ubuntu.com/community/mkusb").

---

### Post by Bucky Ball on 2016-01-02
*Thread moved to **Fedora/RedHat and derivatives**.*

---

### Post by sudodus on 2016-01-03
[mkusb](https://help.ubuntu.com/community/mkusb/gui#Simple_to_test_mkusb_in_linux_distros.2C_which_do_not_manage_an_Ubuntu_PPA) works also in Fedora, but you have to install it [from phillw.net](https://help.ubuntu.com/community/mkusb/gui#from_phillw.net)

---

