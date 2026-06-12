---
title: "Can KVM  run a Windows XP installation on another partition?"
date: 2009-02-09
forum: Desktop Environments
---

### Post by dwschulze on 2009-02-09
I have a dual boot Ubuntu 8.10 / Windows XP system.  I've been reading about the various virtualization options available on Ubuntu 8.10.  According to what I've read I should be able to use KVM to run the Windows XP installation I have on the other partition under KVM.  Sounds great.  I've wanted to do this for over a year.

Last year I tried this using VMWare Workstation for Linux.  VMWare calls this configuration a native disk.  It didn't work.  As soon as I booted the Windows XP guest it blue screened.  VMWare technical support was no help.

I don't want a second installation of Windows XP on a virtual disk.  I want to run the same installation of Windows XP that I can boot into (on a seperate partition) as a guest OS under Ubuntu.

According to what I've read about KVM on other web sites I should be able to do this.  However, when I read the docs on the Ubuntu site about installing guest OSes on KVM, it doesn't sound as good.  The Ubuntu docs talk about booting from a .iso image.  That's not what I want.

Does anyone have a Windows XP guest on another partition running under KVM on Intrepid?  If so, how well does it work?

Thanks.

Dean

---

### Post by dwschulze on 2009-02-10
It looks like the answer is no:

[https://answers.launchpad.net/ubuntu/+question/29481](https://answers.launchpad.net/ubuntu/+question/29481)

Ubuntu has done a real disservice by splitting its support into forums and launchpad.

Wikipedia has this wrong on their web site as well.  I've corrected their page comparing the capabilities of various virtualization options:

[http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines#cite_note-kvm-partition-dual-boot-1](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines#cite_note-kvm-partition-dual-boot-1)

---

### Post by ABCC on 2009-12-17
Haven't tried on Intrepid, but this works on Karmic. The command is:
```

kvm -m 1024 /dev/sda

```

Assuming you boot from /dev/sda you should be able to choose XP (or any other OS) from the bootloader.

---

