---
title: "Adding a kernel module ..."
date: 2006-03-07
forum: Desktop Environments
---

### Post by dbee on 2006-03-07
So I have a problem getting one of the nvidia kernel modules to add into my Kernel...

I think the easiest way to do this is if I just show my bash screen 
```

root@ubuntu64:/home/babo# slocate *nvidia*.ko
/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia.ko

root@ubuntu64:/home/babo# modprobe /lib/modules/2.6.12-9-amd64-generic/kernel/drivers/video/nvidia/nvidia.ko
FATAL: Module /lib/modules/2.6.12_9_amd64_generic/kernel/drivers/video/nvidia/nvidia.ko not found.

root@ubuntu64:/home/babo# modprobe /lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidia.ko
FATAL: Module /lib/modules/2.6.12_10_amd64_generic/kernel/drivers/video/nvidia/nvidia.ko not found.

root@ubuntu64:/home/babo# modprobe /lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko
FATAL: Module /lib/modules/2.6.12_10_amd64_generic/kernel/drivers/video/nvidia/nvidiafb.ko not found.

root@ubuntu64:/home/babo# insmod /lib/modules/2.6.12-9-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko
insmod: error inserting '/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko': -1 Unknown symbol in module

root@ubuntu64:/home/babo# insmod /lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko
insmod: error inserting '/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidiafb.ko': -1 Unknown symbol in module

root@ubuntu64:/home/babo# insmod /lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidia.ko
insmod: can't read '/lib/modules/2.6.12-10-amd64-generic/kernel/drivers/video/nvidia/nvidia.ko': No such file or directory


```
... baiscally insmod either can't read my module or gets an unknown symbol. whereas modprobe says that it's a fatal module 
... why don't insmod and modprobe recognise my nvidia module ? I had to switch t gcc-3.4 to compile the module - but when I switch back to 4.0 - I get the same problem. 
At the moment I have to recompile the module at every bootup in order to startx.

Help !

---

### Post by Ampersand on 2006-03-07
Have you tried getting the drivers from apt? ([https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)) Also, what happens if you just use
```
modprobe nvidia
```

---

### Post by dbee on 2006-03-07
Cool, thanks Ampersand, modprobe nvidia returned without any errors. 

I don't know whether it succeeded or, because I can't reboot my machine for a while now. But I guess there is a chance that it worked ok. 

Is there anyway to check if it worked without having to reboot ?  lspci gives me back a load of unknown devices ... even though I heard that lspci isn't really that useful anyway.

---

