---
title: "How to incrase swap memory ?"
date: 2009-01-02
forum: General Help
---

### Post by jrkraj on 2009-01-02
hi friends,

Please tell me how to increase swap memory i have allocated only 100 m.b

---

### Post by theozzlives on 2009-01-02
You have to shrink a partition and grow the swap. You can do that with partition editor on your live CD.

---

### Post by kgas on 2009-01-02
Why do  you want to increase swap size? 

Read this : [http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)

---

### Post by jrkraj on 2009-01-02
Need more clarification i am very much new to the Linux.

---

### Post by HermanAB on 2009-01-02
You may find that it is easier to use a swap file than to enlarge the swap partition.  Read 'man swapon' and 'man mkswap' for details.  It is not difficult to do.

Cheers,

Herman

---

### Post by Sin@Sin-Sacrifice on 2009-01-02
If anyone is still looking at this thread; I have a question. Is there any reason I've never used more than 40 MB of swap? I have 2 GB RAM and a 2GB swap partition. Reason being that I made a large swap is because I do video editing and conversions and play with other media toys so I figured I'd need it. Apparently not... Is 2GB RAM enough for just about all projects? Aside from Virtualbox and all that...

---

### Post by jrkraj on 2009-01-02
> **Sin@Sin-Sacrifice said:**
> If anyone is still looking at this thread; I have a question. Is there any reason I've never used more than 40 MB of swap? I have 2 GB RAM and a 2GB swap partition. Reason being that I made a large swap is because I do video editing and conversions and play with other media toys so I figured I'd need it. Apparently not... Is 2GB RAM enough for just about all projects? Aside from Virtualbox and all that...

so,100 m.b enough no need to increase.

thanks everybody

---

### Post by cdtech on 2009-01-02
> **Sin@Sin-Sacrifice said:**
> If anyone is still looking at this thread; I have a question. Is there any reason I've never used more than 40 MB of swap? I have 2 GB RAM and a 2GB swap partition. Reason being that I made a large swap is because I do video editing and conversions and play with other media toys so I figured I'd need it. Apparently not... Is 2GB RAM enough for just about all projects? Aside from Virtualbox and all that...

Swap is still coded into the kernel and its a good idea to use some swap space. I have 2G of memory myself and chose to use a swap size of the same. I've noticed during my backups (full system) that I will use around 350M of swap although I have ample amount of RAM.

For anyone interested in increasing their swap here is a procedure for using a swap file. The advantage of swap files is that you don't need to find an empty partition or repartition a disk to add additional swap space. To create a 1GB file, type:
```
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```
/swapfile is the name of the swap file, and the count of 1048576 is the size in kilobytes (i.e. 1GB). Similarly, mount it using the swapon command:
```
swapon /swapfile
```
The /etc/fstab entry for a swap file would look like this:
```
/swapfile       none    swap    sw      0       0
```
Hope this helps.......

---

### Post by jrkraj on 2009-01-02
thanks a ton.

---

### Post by jrkraj on 2009-01-02
```
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```
i try this command but got an error " permission denied"

---

### Post by code_u11 on 2009-01-03
use sudo
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```

---

