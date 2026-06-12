---
title: "How to install kernel sources?"
date: 2009-04-12
forum: General Help
---

### Post by spiceoflife on 2009-04-12
Hello everybody,

actually, i want to install an usb driver but i must firstly install the kernel sources.I have found a problem to install it ,so please  could you please help me!!!

thaks

---

### Post by Thura on 2009-04-12
Could you be more specific ? I don't think kernel sources are necessary for driver installations, must be header files ...

Ok, anyways, if you want to source of kenel,
```
sudo apt-get install kernel-source
```

Or, if you want the header files,
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by spiceoflife on 2009-04-13
> **Thura said:**
> Could you be more specific ? I don't think kernel sources are necessary for driver installations, must be header files ...

Ok, anyways, if you want to source of kenel,
```
sudo apt-get install kernel-source
```

Or, if you want the header files,
```
sudo apt-get install linux-headers-$(uname -r)
```
hi,
thank you or your help.In fact,i'm trying to install a usb driver but firstly i have to download the kernel sources,then modify the driver,compile it and finally insert it into the kernel.So, please could you help me!!

---

### Post by Aubergines on 2009-04-13
If you're compiling anything you might want to install "build-essential" as well.

---

### Post by Slim Odds on 2009-04-13
Compiling the kernel ain't no walk in the park these days....

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Good luck...

---

### Post by spiceoflife on 2009-04-13
hi,
In fact, i need to install these pakages :
  ti_fw_3410.h
_ ti_fw_5052.h
_ ti_usb_3410_5052.c
_ ti_usb_3410_5052.h
 and then i have to do some modifications in:_ ti_usb_3410_5052.c
and finally compile the driver and insert it into my kernel.
So, how can i do this,i didn't arrive to the compilation!!

---

### Post by Thura on 2009-04-13
Doesn't it have readme file ?
[http://www.brimson.com/downloads/ti_usb_release_notes-0.5-1.txt](http://www.brimson.com/downloads/ti_usb_release_notes-0.5-1.txt)
Or it is easier to compile as a patch the kernel ...
Download the ti_usb_*.patch file here ...
[http://www.brimson.com/downloads/](http://www.brimson.com/downloads/)
Then just google on how to patch ...

---

### Post by spiceoflife on 2009-04-14
hi,

i have a problem now, when i taped the command:"dmesg",the following line doesn't appear:

usb 1-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

So, what should i do????????????

---

