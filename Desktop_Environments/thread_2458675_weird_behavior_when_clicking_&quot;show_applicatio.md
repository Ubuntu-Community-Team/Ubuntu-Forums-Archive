---
title: "weird behavior when clicking &quot;show applications&quot;"
date: 2021-03-02
forum: Desktop Environments
---

### Post by ronjjjg8885 on 2021-03-02
hi
when i click on "show applications" i get a screen jump before the list loaded well.
i'm adding a video
[https://ufile.io/s0fbkmnk](https://ufile.io/s0fbkmnk)
let me know if you know this
have a nice day

---

### Post by ActionParsnip on 2021-03-03
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy gnome-terminal

```
Thanks

---

### Post by ronjjjg8885 on 2021-03-04
```
lsb_release -a; uname -a; apt-cache policy gnome-terminal
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.10
Release:    20.10
Codename:    groovy
Linux XXX-H81M-S2H 5.8.0-44-generic #50-Ubuntu SMP Tue Feb 9 06:29:41 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
gnome-terminal:
  Installed: 3.38.0-1ubuntu1.1
  Candidate: 3.38.0-1ubuntu1.1
  Version table:
 *** 3.38.0-1ubuntu1.1 500
        500 http://il.archive.ubuntu.com/ubuntu groovy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.38.0-1ubuntu1 500
        500 http://il.archive.ubuntu.com/ubuntu groovy/main amd64 Packages


```

---

### Post by ActionParsnip on 2021-03-04
If you create a new Ubuntu user and log in as that to the same session type, is it the same?

---

### Post by ActionParsnip on 2021-03-04
I found this but it's a different Gnome version
[https://news.softpedia.com/news/fix-for-gnome-3-36-stuttering-bug-in-the-works-529842.shtml](https://news.softpedia.com/news/fix-for-gnome-3-36-stuttering-bug-in-the-works-529842.shtml)

---

### Post by ActionParsnip on 2021-03-04
What is the output of:
```

sudo lshw -C display

```
Thanks

---

### Post by ronjjjg8885 on 2021-03-12
```
  *-display                 
       description: VGA compatible controller
       product: TU116 [GeForce GTX 1650 SUPER]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:38 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-display
       description: VGA compatible controller
       product: 4th Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:35 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)


```

---

