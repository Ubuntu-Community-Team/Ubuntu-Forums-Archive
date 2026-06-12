---
title: "New Dell Inspiron upgrade to 9.10 no sound"
date: 2010-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chill3570 on 2010-02-01
I just upgraded my new Dell  Insprion  to 9.10.
Now I have no sound.
I have followed other threads and so far no resolution.

Any ideas

       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:21 memory:f6afc000-f6afffff

---

### Post by chill3570 on 2010-02-02
I fixed the issue. I had to install grub2.  Then I was able to boot to the proper kernal. 2.6.31-14-generic.
This brought back my sound.   I did loose my wireless. But I will work on that.

---

### Post by chill3570 on 2010-02-02
I fixed the wirless problem by
did the command line method. Plug in to a wired network connection and run: sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source


and then rebooting.


I am back in business

---

