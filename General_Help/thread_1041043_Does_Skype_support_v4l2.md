---
title: "Does Skype support v4l2?"
date: 2009-01-16
forum: General Help
---

### Post by meindian523 on 2009-01-16
I'm running Ubuntu 8.10 64 bit,and downloaded Skype from their site.I downloaded the Dynamic option,and extracted it into /opt.Everything works except my webcam which is a v4l2 device
```

easwarh@l1nuxr0cks:~$ lsusbeaswarh@l1nuxr0cks:~$ lsusb
Bus 001 Device 003: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
easwarh@l1nuxr0cks:~$ 

```I have downloaded the v4l drivers and compiled them,the webcam (as verified by Cheese)works but only so long as a reboot/hibernate.As far as I've tried,Skype doesn't work with my webcam.

Does Skype work with v4l2 devices?
And does anyone have any explanation to "The case of the missing drivers"?

In short,is the problem of Skype not able to use my webcam,Skype's fault because it can't deal with v4l2 or is it due to the drivers going missing now and then?

I'm real tired of compiling v4l again and again........

---

### Post by Tim Sharitt on 2009-01-16
The Z-Star Microelectronics Corp. ZC0301 WebCam is on the list of know non-working web cams at [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams). 

I don't know what might have change from the ZC0301 to the ZC0305, but there is a good chance you may be fighting a lost cause for now.

---

### Post by meindian523 on 2009-01-16
List of "Fiddle to get Working" webcams has my webcam has the last but one entry,though I'll have to check my Skype version,and the test was with 7.10 (and 64 bit!)
> 
 Vimicro/ZC0305 
    7.10 
    0ac8:305b 
    gspca v. 20071224 
    (AMD64) Works with skype 2.0.0.68  


---

### Post by meindian523 on 2009-01-16
My Skype is 2.0.0.72.
Thanks for the list though.:)

---

### Post by Tim Sharitt on 2009-01-16
Sorry, I didn't know the Vimicro was the same as the one as yours. :)

Do you have the 20071224 version of the gspca driver compiled and installed?

---

### Post by meindian523 on 2009-01-16
I've the gspca-source package from the Ubuntu repositories installed,which is version 01.00.20-1.Which version corresponds to gspca version 20071224 though,I don't know.I have downloaded the source drivers 20071224,and tried to compile them,wherein I ran into this problem:
[http://ubuntuforums.org/showthread.php?t=1015043](http://ubuntuforums.org/showthread.php?t=1015043)
which has a duplicate,as far as I could see,though I didn't verify the error line by line here:
[http://ubuntuforums.org/showthread.php?t=1015611](http://ubuntuforums.org/showthread.php?t=1015611)

whereupon I tried PartyBoi's solution and ran into the error mentioned by sangandongo in the last post.Again,I haven't verified the error line by line.As you can see,there has been no lack of tries. :)](*,)

---

### Post by Tim Sharitt on 2009-01-16
Try this. It may not work, but it may give more information on how to fix it.

Untar a clean version on the tarball in Partyboi2's post and apply the patch.

Instead of using the build script, just run make in the source directory. Post the output if there is an error.

I had no errors building the driver, so it may be an x86_64 issue. Maybe we can come up with a solution by dissecting the errors.

---

### Post by meindian523 on 2009-01-16
```

easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/easwarh/Path1/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/easwarh/Path1/gspcav1-20071224/gspca_core.o
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2466: error: implicit declaration of function &#8216;video_usercopy&#8217;
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c: At top level:
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2607: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2612: error: unknown field &#8216;owner&#8217; specified in initializer
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2612: warning: initialization from incompatible pointer type
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2614: error: unknown field &#8216;type&#8217; specified in initializer
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2772: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:2783: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/easwarh/Path1/gspcav1-20071224/gspca_core.c:4314: error: incompatible types in assignment
make[2]: *** [/home/easwarh/Path1/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/easwarh/Path1/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ 

```

---

### Post by Tim Sharitt on 2009-01-16
Did you apply the patch from [here]("http://ubuntuforums.org/attachment.php?attachmentid=90642&d=1225570823")? asm/semaphore.h is being used, but it should be linux/semaphore.h.

---

### Post by meindian523 on 2009-01-16
```
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ patch < /home/easwarh/Path1/gspca.patch
Path1/
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ patch < /home/easwarh/Path1/gspca.patch
patching file gspca_core.c
patching file gspca.h
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/easwarh/Path1/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/easwarh/Path1/gspcav1-20071224/gspca_core.o
  CC [M]  /home/easwarh/Path1/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /home/easwarh/Path1/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/easwarh/Path1/gspcav1-20071224/gspca.mod.o
  LD [M]  /home/easwarh/Path1/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ 

```
I assume there are no errors.

---

### Post by meindian523 on 2009-01-16
I ran ```
sudo make install -j3
``` and it completed without errors.```
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ sudo make install -j3
[sudo] password for easwarh: 
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ 
```When I run ```
sudo modprobe gspca<Tab>
```,I get,
```
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ sudo modprobe gspca
gspca          gspca_ov519    gspca_sonixj   gspca_spca506  gspca_sunplus
gspca_conex    gspca_pac207   gspca_spca500  gspca_spca508  gspca_t613
gspca_etoms    gspca_pac7311  gspca_spca501  gspca_spca561  gspca_tv8532
gspca_mars     gspca_sonixb   gspca_spca505  gspca_stk014   gspca_vc032x
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ 
```
Which one should I modprobe?Is it gspca_vc032x,because,IIRC[[not sure]],it's the Vimicro driver?

---

### Post by Tim Sharitt on 2009-01-16
Try the generic gspca first. If I understand the code (I may not :)), it should load the correct driver. If that doesn't work then try the gspca_vc032x
.

---

### Post by meindian523 on 2009-01-16
```
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ sudo modprobe gspca_vc032x 
FATAL: Error inserting gspca_vc032x (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/gspca/gspca_vc032x.ko): Unknown symbol in module, or unknown parameter (see dmesg)
easwarh@l1nuxr0cks:~/Path1/gspcav1-20071224$ 

```dmesg gives```
[30305.368034] usbcore: deregistering interface driver gspca
[30305.368798] gspca: driver gspca deregistered
[30317.934538] gspca_vc032x: Unknown symbol gspca_frame_add
[30317.934654] gspca_vc032x: Unknown symbol gspca_debug
[30317.934946] gspca_vc032x: Unknown symbol gspca_disconnect
[30317.935048] gspca_vc032x: Unknown symbol gspca_resume
[30317.935148] gspca_vc032x: Unknown symbol gspca_dev_probe
[30317.935250] gspca_vc032x: Unknown symbol gspca_suspend

```The first two lines of quoted dmesg correspond to ```
sudo rmmod gspca
```

---

### Post by meindian523 on 2009-01-23
bump.

---

### Post by dfehrer on 2009-05-31
So I just entered in that bunch of code that    	meindian523 posted here and now my webcam isn't even working in gstreamer-properties... any ideas how I can fix this?

....I guess i probably shouldn't have done that since I am a noob!:(

---

### Post by meindian523 on 2009-06-01
which particular bunch of code?

---

