---
title: "I cannot get in ubuntu!?"
date: 2009-02-21
forum: General Help
---

### Post by daxy on 2009-02-21
Please help,

I have installing ubuntu 8.04 last 2 days on my hp mini-note 2133.And today when i tryed to get in i insert my user and pass..and show black screen writed:

**"running local boot script(etc/rc.local)"**

...and every time back me on login start page...

I cannot get in and edit anything...:(

Please help!!!!!!!

](*,)

---

### Post by itang sanjana on 2009-02-21
How about this:
[https://answers.launchpad.net/ubuntu/+question/22368](https://answers.launchpad.net/ubuntu/+question/22368)
HTH

---

### Post by daxy on 2009-02-21
> **itang sanjana said:**
> How about this:
[https://answers.launchpad.net/ubuntu/+question/22368](https://answers.launchpad.net/ubuntu/+question/22368)
HTH


Thanks, but how to run ubuntu 8.04 recovery mode???
I boot ubuntu from usb and show:

1.Try ubuntu without any change...
2.Install Ubuntu
3.Check filesystem for defect(i run it and nothing changed it)
4.Test memory
5.Boot from first hard disk

...what to choose???

Thanks

---

### Post by itang sanjana on 2009-02-21
Try again the way you mentioned in first post.
Before you get asked for the username & password,
there is a GRUB load,
press esc before the countdown end,
select run recovery mode and enter
HTH

---

### Post by daxy on 2009-02-21
Thanks, but seems that recovery mode doesn´t help me.I tryed everything in recovery and nothing solve my problem...:cry::cry::cry:

---

### Post by daxy on 2009-02-22
I follow tutorial in [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

how to install ubuntu 8.04 on my hp 2133 but there is one thing that i can´t do from tutorial:

1.) Video and CPU Scaling Fixes -- Back in Terminal, type the following:

sudo gedit /boot/grub/menu.lst

This will bring up the grub boot menu configuration file. Scroll to the bottom of the file and you'll find several boot options. Go to the first, titled "Ubuntu 8.04.1, kernel 2.6.24-19-generic" and in the "kernel" line, delete "xforcevesa". In its place, type:

acpi_osi="!Windows 2006"

This will enable CPU speed scaling, helping preserve the Mini-Note's already limited battery life. For more information about this bug (which is in the kernel, and not specific to the Mini-Note) see this link. Save the file and exit gedit.

...i open menu.1st but and get to kernel line but there is no "xforcevesa" to change with acpi_osi="!Windows 2006"


...maybe is that reaseon of that problem...PLEASE HELP, I like to work with UBUNTU but that stops me!!!!!!!!!

---

### Post by itang sanjana on 2009-03-03
Seems like there is nothing else I can do to help.
Sorry :(

---

