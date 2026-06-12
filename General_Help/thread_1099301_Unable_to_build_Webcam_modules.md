---
title: "Unable to build Webcam modules"
date: 2009-03-18
forum: General Help
---

### Post by bcschmerker on 2009-03-18
After reinstalling 7.10 for a new system board on my Everex mid-tower (now equipped with an AMD Athlon 64 X2 MPU and nVIDIA integrated chipset in for an all-VIA rig), I ran into fatal errors attempting to build both the OV51x and SPCA5xx Modules for Kernel 2.6.22-16rt from the Source packages, using the Module Assistant with current versions (as of 18 March 2009) of all requisite packages (including build-essential, which I installed from CD using GDebi to bypass a bug in Synaptic Package Manager after Synaptic failed to locate that package online).  Apparently at least one variable needed for both Modules is not being passed from other Kernel Headers.  How does one go about tracing this problem?

Additionally, I ran into the same problem(s) after a successful upgrade to 8.04-LTS, when using Source packages for Kernel 2.6.24-23.48rt.  It appears as though I will also have to amend at least one Makefile to fix a deprecated variable label that /usr/bin/make had caught during the Clean procedure, tagging with Error 2.

---

### Post by bcschmerker on 2009-04-06
If it helps anyone figure out how to diagnose my issues, the following StdOut+StdErr returned after I fixed /usr/src/modules/gspca/Makefile (viz. updating CFLAGS to EXTRA_CFLAGS), using Make from /usr/src/modules/gspca: 

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-rt'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:2567: error: unknown field 'hardware' specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function 'cd_to_spca50x':
/usr/src/modules/gspca/gspca_core.c:2616: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c: In function 'spca50x_create_sysfs':
/usr/src/modules/gspca/gspca_core.c:2655: warning: passing argument 2 of 'video_device_create_file' from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2657: warning: passing argument 2 of 'video_device_create_file' from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2659: warning: passing argument 2 of 'video_device_create_file' from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2665: warning: passing argument 2 of 'video_device_remove_file' from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2667: warning: passing argument 2 of 'video_device_remove_file' from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2669: warning: passing argument 2 of 'video_device_remove_file' from incompatible pointer type
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-rt'
make: *** [default] Error 2
```What field "hardware" is referred to at Line 2567?  What pointer type is actually expected for both the Initialization at Line 2616 and the Procedure video_device_create_file referenced in Lines 2655 et seq.?

---

### Post by zulek87 on 2009-04-28
I got same issue here.

I'm using ubuntu 9.04 official edition and I had to change my kernel and headers due to high cpu usage from **2.6.28**  to **2.6.30-020630rc2-generic **and** xserver-xorg-video-intel **from **2.4 **to** 2.7.1**.  (flash +intel graphic card =** [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)**)

After that I tried to compile  **ov51x-jpeg-1.5.9 **and i got:

$ make

[html]
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.30-020630rc2-generic'
  CC [M]  /home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ?create_proc_ov511_cam?:
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ?info?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: ?struct proc_dir_entry? has no member named ?owner?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: ?struct proc_dir_entry? has no member named ?owner?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: ?struct proc_dir_entry? has no member named ?owner?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: ?struct proc_dir_entry? has no member named ?owner?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ?proc_ov511_create?:
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: ?struct proc_dir_entry? has no member named ?owner?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ?ov51x_clear_snapshot?:
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function ?warn?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ?ov51x_v4l1_ioctl?:
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ?video_usercopy? from incompatible pointer type
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ?video_usercopy? makes integer from pointer without a cast
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ?video_usercopy? makes pointer from integer without a cast
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function ?video_usercopy?
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[2]: *** [/home/gk/Sterowniki/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/gk/Sterowniki/ov51x-jpeg-1.5.9] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.30-020630rc2-generic'
make: *** [all] B&#322;&#261;d 2 [/html]when I did it when I was using **2.6.28** kernel and headers everything was OK... now is not OK... I had similar issue with   **ov51x-jpeg-1.5.8 **and **2.6.x** kernel and the solution was to wait for   **ov51x-jpeg-1.5.9... **


P.S.
I don't want gspca module coz I have inverse LED shining and don't want to preload module....


Any solutions?>

---

