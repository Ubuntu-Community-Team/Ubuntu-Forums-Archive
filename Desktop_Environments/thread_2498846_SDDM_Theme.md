---
title: "SDDM Theme"
date: 2024-06-30
forum: Desktop Environments
---

### Post by sratledge on 2024-06-30
I would like to use Sweet Ambar Blue theme but on my Kubuntu  system, it gives me an error message something about the theme cannot be  loaded and no version.   I have tried some stuff I found on reddit and  stuff but nothing has helped.  I tried a couple other themes, same error. Any suggestions? 


Operating System: Kubuntu 24.04 
KDE Plasma Version: 5.27.11 
KDE Frameworks Version: 5.115.0 
Qt Version: 5.15.13 
Kernel Version: 6.8.0-36-generic (64-bit) 
Graphics Platform: X11 
Processors: 16 × AMD Ryzen 7 3700X 8-Core Processor 
Memory: 31.3 GiB of RAM 
Graphics Processor: NVIDIA GeForce RTX 2060/PCIe/SSE2 
Manufacturer: Alienware 
Product Name: Alienware Aurora Ryzen Edition 
System Version: 2.7.0

---

### Post by ActionParsnip on 2024-07-01
Does this help. You can check your config here
[https://wiki.archlinux.org/title/SDDM](https://wiki.archlinux.org/title/SDDM)

---

### Post by sratledge on 2024-07-01
No, but I think I am missing some sort of dependencies but then when I run apt I get back that I already have it or it says it can't find what I asked for.

---

### Post by sratledge on 2024-07-01
Hey I made some progress here (finally).   One issue was that the sddm.conf file was screwed up or empty.   I still can't get the original theme I picked out working but I found that Breeze works as well as the C64 theme, so I am going with that for now.
In case it's needed again down the road you want to run:
sudo su
sddm --example-config > /etc/sddm.conf

---

### Post by ActionParsnip on 2024-07-01
Why the su? Why not just use
```

sudo sddm --example-config > /etc/sddm.conf

```
Then it's one command rather than two. Does exactly the same thing

---

