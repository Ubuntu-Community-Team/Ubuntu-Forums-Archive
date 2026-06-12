---
title: "JAunty webcam issues"
date: 2009-04-26
forum: General Help
---

### Post by hvc123 on 2009-04-26
Hi all,

i am trying to get my logitech quickcam express running and when i build the gspca driver all is well but as soon as i modprobe it i get these errors


"sudo modprobe gspca
WARNING: All config files need .conf: /etc/modprobe.d/linux-wlan-ng, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lrm-video, it will be ignored in a future release."

here is my dmesg

"[ 2881.780805] usbcore: registered new interface driver gspca
[ 2881.781081] /usr/src/modules/gspca/gspca_core.c: gspca driver 01.00.20 registered"

and here is dmesg when i unplug the webcam and plugit back in 

"[ 3459.680447] usb 2-2: USB disconnect, address 4
[ 3462.058736] usb 2-2: new full speed USB device using ohci_hcd and address 7
[ 3462.268757] usb 2-2: configuration #1 chosen from 1 choice"



i dont get the /dev/video created either

can anyone shed any light ?

thanks

---

### Post by spiderbatdad on 2009-04-26
did you patch the driver using the patch here? [http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500](http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500)

```
gunzip gspca.patch.gz
```

which will create gspca.patch

cd into the gspca directory

```
cd gspcav1-20071224

```
then apply the patch:

```
patch < ../gspca.patch
```

gspca should compile now and correctly install when you run

sudo ./gspca_build

make sure to remove gspca_main module. Assuming you are re-building gspca from source, as it was broken in the repos last time i tried to use it.
Good luck.

---

### Post by hvc123 on 2009-04-26
thanks for that. i tried the walkthrough and i cant compile... this is the output

" /usr/src/modules/gspca ]$ sudo ./gspca_build

 REMOVE the old module if present

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory
WARNING: All config files need .conf: /etc/modprobe.d/linux-wlan-ng, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lrm-video, it will be ignored in a future release.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-powerpc'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:29: error: linux/semaphore.h: No such file or directory
In file included from /usr/src/modules/gspca/gspca_core.c:64:
/usr/src/modules/gspca/gspca.h:17:30: error: media/v4l2-ioctl.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c:2615: error: unknown field âvfl_typeâ specified in initialiser
/usr/src/modules/gspca/gspca_core.c: In function âspca50x_create_sysfsâ:
/usr/src/modules/gspca/gspca_core.c:2773: warning: passing argument 1 of âdevice_create_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2776: warning: passing argument 1 of âdevice_create_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2779: warning: passing argument 1 of âdevice_create_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2784: warning: passing argument 1 of âdevice_remove_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2786: warning: passing argument 1 of âdevice_remove_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2788: warning: passing argument 1 of âdevice_remove_fileâ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c: In function âspca5xx_probeâ:
/usr/src/modules/gspca/gspca_core.c:4315: error: incompatible types in assignment
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-powerpc'
make: *** [default] Error 2
"


OK 
REDOWNLOADED the source code. now it compiles.. i can load the driver yet it STILL does not create the /dev/video

head dooooooer

---

### Post by spiderbatdad on 2009-04-26
I know what  you mean...try this site and also read comments for some critical step you've missed. You must be getting close:
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

---

### Post by hvc123 on 2009-04-26
head mess man... 

the module is loaded fine but it still does not create the /dev/video. 

i tried the link and folloed the steps and still it is not created.

maybe its just not going to work on my ppc hardware.

thanks  though

---

### Post by spiderbatdad on 2009-04-26
oh...ppc! yeah, you'll need a mac compliant cam i guess.

---

