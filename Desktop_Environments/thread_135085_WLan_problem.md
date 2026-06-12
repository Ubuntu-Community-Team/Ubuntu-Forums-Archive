---
title: "WLan problem"
date: 2006-02-23
forum: Desktop Environments
---

### Post by thor erik on 2006-02-23
Hey
i got this Jensen Scandinavia Wireless Notebook card II withc should be ok to set up on linux(cause i did it on knopix :rolleyes: )
but i could't find any way to make it work on ubuntu so i downloaded the drivers for it
and read the readme where it say:
> (0)Make sure the C-compile version. Run "gcc -v".
       If gcc version is 2.xx, use release driver RTL8180_24x_RH73.zip.
       If gcc version is 3.xx, use release driver RTL8180_24x_RH90.zip.

	(1)Modify macros in Makefile.
         KERNELRELEASE - represent kernel release version
         IO_FLAGS - pci I/O space mapping
         ENDIAN_FLAGS - big/little endian
         OP_MODE_FLAGS - Operation on either AP or Client mode
         DRV_FLAGS - Driver debugging messge ...etc.

1. i dnt have 3.xx i got 4.xx O_o
2. where can i find the kenerl release for my linux 
3. wtf!!! what's IO_flags?
4. (same as above just endian :-k )
5. what's AP:???: 


and when i look into the makefile i see this at the top line:
> #-----------------------------------------------
#Specify kernel version and include path
#-----------------------------------------------
KERNELRELEASE=2.4.20-8
INCLUDEPATH=-I /usr/src/linux-$(KERNELRELEASE)/include/

i just had a look in the /usr/src/ folder where it apperantly ended :-k :-k :-k :-k 
so how can i in ANY way make to install this "crappy" card :cry:

---

### Post by dotman on 2006-02-23
well to find your kernel release you type:

```
uname -r
```

if there is nothing in your /usr/src/ folder you may need to download the kernel headers

```
sudo apt-get install linux-headers-'uname -r'
```

replace 'uname -r' with your kernel version

---

