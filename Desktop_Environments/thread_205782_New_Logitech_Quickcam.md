---
title: "New Logitech Quickcam"
date: 2006-06-29
forum: Desktop Environments
---

### Post by jimarko on 2006-06-29
Hi All,

I don't have the USB ID number (I'll add that later this evening, but i think its 0x0928), but I have a Logitech Quickcam, and every time I try to test it in GnomeMeeting or AMSN, it locks my computer COMPLETELY. Not even the mighty CTRL+ALT+DEL or CTRL+ALT+F1 can save me.

I've seen that the link below has my Logitech cam as able to work, but i've tried following the instructions, but it still crashes.

The link: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)


I am probably doing something wrong, but if you could assist me in getting that sorted, I would love y'all for it :D


Jimmy

---

### Post by ericesque on 2006-06-29
last I heard webcam support was simply sketchy at best for linux.  I hope things have changed since I checked last.  I'd be interested to hear what others have to say as well...

---

### Post by loell on 2006-06-29
well, my old logitech qiuckcam express works flawlessly on Dapper ..O:)

---

### Post by jimarko on 2006-06-29
Quote me if you will, but if Dapper Drake was a girl, I'd marry it.


I spoke before I tested it 6.0.6, and it works!!!!!!

ZOMG.

---

### Post by Kratos on 2006-09-10
Glad you had such great luck, but I seem to be on the short end of the rope as far as this is concerned. 

Just bought a brand new QuickCam Express. Here's the lsusb output.

```
Bus 003 Device 003: ID 046d:092f Logitech, Inc.
```

A unique Product ID that I don't see listed on any pages anywhere. Most likely the newest model, guaranteed not to work with Linux for another 10 years. 

I've installed spca5xx and v4l, but xawtv gives me gripes.

```
$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-26-386)
xinerama 0: 1280x1024+0+0
xinerama 1: 1280x1024+1280+0
WARNING: Your X-Server has no DGA support.
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no video grabber device available
```

I'm probably missing something. But, any advice, condolences, or other forms of pity are accepted. If I don't have any luck in the next few days, I'll keep my reciept and packaging handy and return it to WalMart.

---

### Post by allenmaher on 2006-09-11
](*,) 

Well I bought the Logitech Quickcam Chat after reading that others got it working... and well, it is not for me.

```
Bus 001 Device 002: ID 046d:092e Logitech, Inc.

```

I followed the advice on this and other threads and although the spca5xx seems to install and load ok

```
al@marge:~$ lsmod
Module                  Size  Used by
spca5xx               653808  0
videodev               10144  1 spca5xx
usbcore               139076  5 spca5xx,usbhid,ehci_hcd,uhci_hcd

```

It gives me no love and /dev/video0 or video anything does not show up. 

I have tried the included spca5xx driver, compiled the newest 20060501 version, with and without gcc 3.4.  The end result seems the same... I have tried the 386 and 686 kernel... and I have an up to date 6.06 lts installed.

Any other ideas?...

---

### Post by allenmaher on 2006-09-12
OK the reason this cam won't work easily is that the device ID is not recognized by the spca5xx driver.

If you have the source code from the site you can recompile it after editing spca561.h and spca5xx.c duplicating the 0x092c enties (the old version of the cam) and then recompiling and installing... it works but not perfectly, there are some minor diferences between the two,  I will play with some settings and see if I can improve it.

It does work in 352x288 by doing this, but you can't get 640x480 stills.

---

### Post by fragos on 2006-09-15
> **allenmaher said:**
> OK the reason this cam won't work easily is that the device ID is not recognized by the spca5xx driver.

If you have the source code from the site you can recompile it after editing spca561.h and spca5xx.c duplicating the 0x092c enties (the old version of the cam) and then recompiling and installing... it works but not perfectly, there are some minor diferences between the two,  I will play with some settings and see if I can improve it.

It does work in 352x288 by doing this, but you can't get 640x480 stills.

I found two places spca5xx.c to edit for 0x092e, well see if that fixes stills.

---

### Post by fragos on 2006-09-15
Aparently others have had success compiling the spca5xx-20060501 driver.  I get the following when I do make and can't figure what I missed.

fragos@Geo:~/bin/Quickcam Chat/spca5xx-20060501$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/fragos/bin/Quickcam Chat/spca5xx-20060501 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** No rule to make target `Chat/spca5xx-20060501'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [default] Error 2

---

### Post by joao82 on 2006-09-28
> **jimarko said:**
> Hi All,
...
The link: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
...
I am probably doing something wrong, but if you could assist me in getting that sorted, I would love y'all for it :D

Jimmy

hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

---

### Post by ahood on 2006-09-30
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

Thank you so much joao82. Your instructions worked like a charm.

---

### Post by Wesseli on 2006-10-02
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

This worked for me! Finally, thanks dude. My camera is Logitech Quickcam Express, ID is: 046d:092f Logitech, Inc. And Ubuntu Dapper 6.06 also.

Regards,
Wesseli (one week with Linux-only :mrgreen: )

---

### Post by zpon on 2006-10-23
Just tried gspca as well (after compiling spca5xx-20060501 and $ sudo modprobe spca5xx), and now my cam works :D, at least in camorama and spcaview in 352x288. Thanks :).

my device id is 
>  Bus 002 Device 002: ID 046d:092f Logitech, Inc.

---

### Post by Kratos on 2006-10-24
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D


I proceed to give you 1000 large chocolate chip cookies for this lovely tip. :)

---

### Post by joao82 on 2006-10-25
much appreciated :D
I'm glad to see it's working so well to everyone. yw yw

---

### Post by cyberpunk79 on 2006-10-28
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

I tried both the source and apt-get with no avail.  I am using a Logitech QuickCam 'for Notebooks Delux'

```
/dev $ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 007: ID 046d:08d8 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

```

```
 $ lsmod | grep spca
spca5xx               630928  0
gspca                 620688  0
videodev                9856  2 spca5xx,gspca
usbcore               130820  10 spca5xx,gspca,snd_usb_audio,snd_usb_lib,visor,usbserial,usbhid,ehci_hcd,ohci_hcd

```

---

### Post by Kratos on 2006-10-30
> **cyberpunk79 said:**
> I tried both the source and apt-get with no avail.  I am using a Logitech QuickCam 'for Notebooks Delux'

```
/dev $ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 007: ID 046d:08d8 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

```

```
 $ lsmod | grep spca
spca5xx               630928  0
gspca                 620688  0
videodev                9856  2 spca5xx,gspca
usbcore               130820  10 spca5xx,gspca,snd_usb_audio,snd_usb_lib,visor,usbserial,usbhid,ehci_hcd,ohci_hcd

```

I would recommend either the [qc-usb]("http://packages.ubuntu.com/dapper/misc/qc-usb-source") (ubuntu.com) or the [quickcam]("http://qce-ga.sourceforge.net/") (sourceforge.net) drivers. I know looking at [this]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras?highlight=%28Webcams%29") (wiki.ubuntu.com) wiki-page gives you a good starting place.

---

### Post by amhirsch on 2006-11-07
I have reviewed the links and found that according to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) that the Logitech Quickcam Notebook Deluxe (046d:08d8 Logitech, Inc.) is supported by the spca5xx/LE packages.  According to [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) I have downloaded the gspcav1-20060926.tar.gz and installed the module.  

However after installing the module and running modprobe gspca, and checking that the gspca module is loaded, I am not able to access the camera.  There are no video devices in /dev.

Below are relative modules/usb devices recognized/and output from /var/log/messages:

root@amh-ltp:~# lsmod | grep gspc
gspca                 661328  0
videodev               14208  1 gspca
usbcore               167840  8 gspca,snd_usb_audio,snd_usb_lib,ndiswrapper,hci_usb,ehci_hcd,ohci_hcd

root@amh-ltp:/etc/modprobe.d# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:08d8 Logitech, Inc.
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:011d Hewlett-Packard
Bus 001 Device 001: ID 0000:0000

Nov  7 22:38:32 localhost kernel: [ 1416.830653] usb 2-4: new full speed USB device using ohci_hcd and address 4
Nov  7 22:38:32 localhost kernel: [ 1416.903978] usb 2-4: configuration #1 chosen from 1 choice
Nov  7 22:38:42 localhost kernel: [ 1420.768941] Linux video capture interface: v1.00
Nov  7 22:38:43 localhost kernel: [ 1420.774354] usbcore: registered new driver gspca
Nov  7 22:38:43 localhost kernel: [ 1420.774406] /usr/src/gspcav1-20060925/gspca_core.c: gspca driver 01.00.04 registered

Am I having a cranial flatuant?  Anyone have any ideas?

Note:  I am using 6.10

TIA!

---

### Post by fragos on 2006-11-08
It sounds like you didn't follow the install instructions which were to run gspca_build.  That script runs a number of steps including the modprobe.

---

### Post by amhirsch on 2006-11-08
As I had originally upgraded from 6.06 to 6.10 I performed a fresh 6.10 install this morning.  I downloaded the gspcav1-2006925 again and ran gspca_build...below are the results:

root@amh-ltp:/usr/src/gspcav1-20060925# ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        Modules.symvers

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

 LOAD gspca in memory

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20060925 CC=cc mo
dules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/gspcav1-20060925/gspca_core.o
  CC [M]  /usr/src/gspcav1-20060925/decoder/gspcadecoder.o
  LD [M]  /usr/src/gspcav1-20060925/gspca.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/gspcav1-20060925/gspca.mod.o
  LD [M]  /usr/src/gspcav1-20060925/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

So it looks like everything ran properly and when I run an lsmod I see:

root@amh-ltp:/usr/src/gspcav1-20060925# lsmod | grep gspc
gspca                 661328  0
videodev               14208  1 gspca
usbcore               167840  6 gspca,ndiswrapper,hci_usb,ehci_hcd,ohci_hcd

After verifying that the module was loaded I plugged in the camera and verified it was seen by looking at the messages file:

root@amh-ltp:/usr/src/gspcav1-20060925# tail -f /var/log/messages
Nov  8 10:40:18 amh-ltp kernel: [ 2684.593558] Linux video capture interface: v1                                                                                .00
Nov  8 10:40:18 amh-ltp kernel: [ 2684.600583] usbcore: registered new driver gs                                                                                pca
Nov  8 10:40:18 amh-ltp kernel: [ 2684.600590] /usr/src/gspcav1-20060925/gspca_c                                                                   ore.c: gspca driver 01.00.04 registered

With all this being said I still don't have any video devices in dev.  I even tried mknod, but still no dice.

Any other ideas? 

TIA!

---

### Post by amhirsch on 2006-11-08
I looked around and found: [http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)   

Which in looking at the date is newer than the gspca-20060925.tar.gz file that many people are using.

Download this file, uncompress it, change directories into gspca-20060930/gspcav1, and run the gspca_build script.  This popped my Logitech QuickCam Notebook Deluxe up right away. 

My usb info for the QuickCam is:  046d:08d8

I hope this helps others!

;)

---

### Post by fragos on 2006-11-09
Is your web cam plugged into a USB port?  Many USB mount points only exist while the device is live.  You could also go back to the site where you got the driver.  The developer responded to a question I had.

---

### Post by ekravche on 2006-11-09
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

Worked like a charm. I had to include the kernel headers in order to compile the lib though.

Thank you! :D

---

### Post by dannemil on 2006-11-24
> **amhirsch said:**
> I looked around and found: [http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)   

Which in looking at the date is newer than the gspca-20060925.tar.gz file that many people are using.

Download this file, uncompress it, change directories into gspca-20060930/gspcav1, and run the gspca_build script.  This popped my Logitech QuickCam Notebook Deluxe up right away. 

My usb info for the QuickCam is:  046d:08d8

I hope this helps others!

;)


dude, I had been banging my head against the wall for a week trying to get my web cam working. Your instructions finally made it work. Big thanks.

Jim

---

### Post by joao82 on 2006-11-28
> **amhirsch said:**
> I looked around and found: [http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)   

Which in looking at the date is newer than the gspca-20060925.tar.gz file that many people are using.

Download this file, uncompress it, change directories into gspca-20060930/gspcav1, and run the gspca_build script.  This popped my Logitech QuickCam Notebook Deluxe up right away. 

My usb info for the QuickCam is:  046d:08d8

I hope this helps others!

;)

Well, when I wrote my first post here, it was on 28th September pointing to the 20060925 file. That newer file only got out two days later :D in my defense, I can say time doesn't stand still hehe

---

### Post by FingerPie on 2006-12-03
I have been reading through several threads on installing logitech quickcams.  I have a "Desktop" camera, vendor = 046d, product 08c3.  I downloaded gspav1 to my desktop from [http://mxhaard.free.fr/spca50x/Investigation/Gspca/](http://mxhaard.free.fr/spca50x/Investigation/Gspca/).

I extracted the file and went into the folder (in terminal) and typed "gspca_build".  Nothing happens (command not found).  I tried "sudo ./gspca_build" and got a FATAL error about a kernel.


I tried typing make in the directory and nothing happened.

Could someone point me in the right direction?

-FP

---

### Post by fragos on 2006-12-03
Its been a while since I did this.  Running gspca_build is all I had to do on Ubuntu 6.10.  That file needs to have permissions set to execute.  I don't however recall having to explicitly do that.  The first thing that script does to to check for root and it comes back telling you so.  Perhaps the reason that didn't respond was because you didn't "./gspca_build".  I checked  it to make sure of the behavior.  Was the fatal error from Linux or the script and what's the exact wording of the error?

---

### Post by FingerPie on 2006-12-11
sorry for the delay.

I am pretty sure i got it to  build.  Still no cam in VLC or ekiga.  

I compiled from a folder on the desktop, should i have had the folder soewhere else?

-FP

---

### Post by fragos on 2006-12-11
Go to Ekiga Preferences-> Devices-> Video Devices.  Video Plugin should be V4L.  Camera should now be listed in the Input devices, Format "Auto" and Channel is probably 0 which refers to /dev/video0.
In Codecs-> Video Codecs enable video support.  Worked for me with a new Quickcam Chat.

---

### Post by FingerPie on 2006-12-13
Ekiga:
"Error while opening video device USB Video Class device"

Not detected.

oh well.

---

### Post by fragos on 2006-12-13
You might also try camorama which is only a web cam viewer that worked with the driver you're using.  It is simpler and may be easier to get running.

---

### Post by FingerPie on 2006-12-27
thanks for help.  Still no dice.  I am playing with it as i get time.  I'll post any luck.

---

### Post by mikeyman on 2007-01-04
Thank you all...it worked like a charm in Kopete.

Compile it with root or sudo and it just works. I have tested it under Dapper and Edgy and they both worked well under Kopete and WengoPhone, so I am guessing it will work under anything that looks for a USB camera.

Big thanks to all who worked on this.

---

### Post by scadieux on 2007-01-09
Worked flawlessly for my brand new QuickCam Deluxe for Notebooks. Thanks.

---

### Post by Gsyman on 2007-01-15
Tried the gspca with a logitech Webcam Chat (ID 046d:092e Logitech, Inc.) but when lauching camorama i get 'could not connect to video device /dev/video0 please check connection'. It is connected OK you can see it when running lsusb.
What should I try next?
Thanks

---

### Post by fragos on 2007-01-15
Camorama assumes /dev/video0 but can be started for other video devices.  Open a terminal and with the chat connected do "ls /dev/video*" and see if there's a video1.  I have a TV card which also mounts to video*.  Sometimes the TV is video0 and sometimes video1 which is a bit of a pain since I have to edit configurations for both my TV ap and webcam.  I have the same webcam as you do.

---

### Post by davholla on 2007-01-24
I have Ubuntu 6.0.6 and am trying to use the driver from 
[http://mxhaard.free.fr](http://mxhaard.free.fr) and I get this error :-

```

root@david-desktop:/gspcav1-20070110# ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

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
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/gspcav1-20070110 CC=cc modules
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 11: cc: command not found
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 12: cc: command not found
make[1]: cc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /gspcav1-20070110/gspca_core.o
/bin/sh: cc: command not found
make[2]: *** [/gspcav1-20070110/gspca_core.o] Error 127
make[1]: *** [_module_/gspcav1-20070110] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2

```

Any ideas ? The driver is gspcav1-20070110.tar.gz

---

### Post by jimarko on 2007-01-24
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory

In regards to the above messages, I think that it might be worth checking out the following:

[LIST]
[*]Does the file gspca.ko exist in /lib/modules?
[*]Do you have write permissions to /lib/modules? (check using ls -la in /lib)
[/LIST]

If write permissions are your issue, execute gspca_build using sudo. (i.e sudo gspca_build)
EDIT: I just noticed in your code dump that you were already logged in as root...



Anyway, hope that helps!
Jimarko

---

### Post by loell on 2007-01-24
> **davholla said:**
> I have Ubuntu 6.0.6 and am trying to use the driver from 
[http://mxhaard.free.fr](http://mxhaard.free.fr) and I get this error :-

```

root@david-desktop:/gspcav1-20070110# ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

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
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/gspcav1-20070110 CC=cc modules
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 11: cc: command not found
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 12: cc: command not found
make[1]: cc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /gspcav1-20070110/gspca_core.o
/bin/sh: cc: command not found
make[2]: *** [/gspcav1-20070110/gspca_core.o] Error 127
make[1]: *** [_module_/gspcav1-20070110] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2

```

Any ideas ? The driver is gspcav1-20070110.tar.gz

seems to me that haven't installed the compiler yet

do ```
sudo aptitude install build-essential 
```

---

### Post by fragos on 2007-01-24
Use "sudo ./gspca_build" after installing "build-essential"

---

### Post by davholla on 2007-02-05
> **fragos said:**
> Use "sudo ./gspca_build" after installing "build-essential"

Thank you all very much I think that has worked.
I would have replied before but I had funerals and things.

---

### Post by fragos on 2007-02-05
The business of life frequently takes precidence over those things we enjoy most.  Please allow me to extend my condolences.  Knowing your life has been full makes the Thank you all the more special.

---

### Post by Blackross on 2007-05-06
i have a Creative webcam NX and a X-eye usb camera... i run  gqcam from apt-get installing and it doesnt find either one, and the right spca5XX is loaded etc... i went and tried to compile from source and i get...


/gspcav1-20070426$ sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xxspca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/drblackross/gspcav1-20070426 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/drblackross/gspcav1-20070426/gspca_core.o
/home/drblackross/gspcav1-20070426/gspca_core.c: In function âspca50x_create_sysfsâ:
/home/drblackross/gspcav1-20070426/gspca_core.c:2630: error: void value not ignored as it ought to be
/home/drblackross/gspcav1-20070426/gspca_core.c:2632: error: void value not ignored as it ought to be
/home/drblackross/gspcav1-20070426/gspca_core.c:2634: error: void value not ignored as it ought to be
make[2]: *** [/home/drblackross/gspcav1-20070426/gspca_core.o] Error 1
make[1]: *** [_module_/home/drblackross/gspcav1-20070426] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make: *** [default] Error 2

even though it finds it 
$ lsmod | grep spc
spca5xx               630928  0
videodev                9856  1 spca5xx
usbcore               130820  3 spca5xx,uhci_hcd

$ lsusb
Bus 001 Device 002: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 001 Device 001: ID 0000:0000

nope nothing

but i did get it to work with my viewpoint 3.1 (toy) camera.... :)
$xawtv -noxv
worked great...

---

### Post by fragos on 2007-05-07
My compile and install went without a hitch.  Check the readme stuff in the tar ball.  You may be missing a compile dependancy.  If that doesn't help, the author is at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html).

---

### Post by Blackross on 2007-05-07
well all i use them for is my telescope... but the viewpoint is the one i kinda want to use all the time.... i'll figure it out. 

the laptop is a CF-27, with a telescope its a nice tough portable setup.. for camping

i had to load the 2.6.*-386 kernel and headers, still nothing but maybe if since i got the viewpoint working with xawtv then maybe i can get other things running (albeit painfully slightly slow) but to cap every so often is ok.

---

### Post by peregrine on 2007-11-08
So I have a logitech qc for notebooks, tried compileing the thing and I got this error.

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jason/Desktop/gspca-20060930/gspcav1 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jason/Desktop/gspca-20060930/gspcav1/gspca_core.o
/home/jason/Desktop/gspca-20060930/gspcav1/gspca_core.c:36:26: error: linux/config.h: No such file or directory
/home/jason/Desktop/gspca-20060930/gspcav1/gspca_core.c: In function &#8216;gspca_init_isoc&#8217;:
/home/jason/Desktop/gspca-20060930/gspcav1/gspca_core.c:1036: warning: assignment from incompatible pointer type
make[2]: *** [/home/jason/Desktop/gspca-20060930/gspcav1/gspca_core.o] Error 1
make[1]: *** [_module_/home/jason/Desktop/gspca-20060930/gspcav1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
```

anyone got an idea of whats going on? Ive got build-essential in it. Some people have said something about headers but ive got no idea how to do that :).

THanks.

---

### Post by fragos on 2007-11-08
Open synaptic and do a search on "linux-headers".  You appear to have an older version of Ubuntu -- you're missing out on a lot of great new stuff.  There will be a number of matches but the you'll need, for Gutsy, will end in "-generic".

---

### Post by peregrine on 2007-11-08
I'm using 7.10. the lusb says

Bus 003 Device 002: ID 046d:08dd Logitech, Inc. 

Sooo its supposed to be supported cause its a Logitech QuickCam for Notebooks.

Thanks a ton for te help.

---

### Post by Lothas on 2007-11-09
Hi, I have the Lego Mindstorms camera. It's a Logitech Quickcam and the lsusb output is:
Bus 001 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web

Gutsy already recognizes (apparently) the camera and the built in microphone but so far I haven't been able to make it work with any of the pre-installed Ubuntu software. Are there any extra configuration steps that I should know about?

---

### Post by masingerz on 2007-11-16
> **joao82 said:**
> hi! just wanted to say that thanks to this thread and mostly the link you gave, I could perfectly install my logitech quickcam express.
don't really know how... but  first i tried the debian package [http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and nothing showed up on vlc capture or amsn. but then i downloaded the source [http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20060925.tar.gz) and compiled it doing "sudo ./gspca_build" and everything went ok :) now i can see my webcam working in vlc and amsn in Ubuntu Dapper 6.06

thank you so much :D

I installed spca5xx-source using synaptic and I went to this web: 

[http://mxhaard.free.fr/spca50x/Download/oldrelease/?S=D](http://mxhaard.free.fr/spca50x/Download/oldrelease/?S=D)

and I downloaded the latest  gspcav1 which is: [http://mxhaard.free.fr/spca50x/Download/oldrelease/gspcav1-20070426.tar.gz](http://mxhaard.free.fr/spca50x/Download/oldrelease/gspcav1-20070426.tar.gz)

(notice with time newer versions should surface).

I did: "sudo ./gspca_build"

my webcam worked, I saw that it worked in ekiga and It worked in amsn too. thank you to joao82
my logitech quickcam "lsusb" output is:

Bus 004 Device 005: ID 046d:0928 Logitech, Inc. Quickcam Express

@@@The only difference with the instructions in the quote is the gspcav1 version date.
BTW im using Gutsy 7.10 :: 2.6.22-14-generic

---

### Post by Lothas on 2007-11-17
Hi, I just tried installing the gspca... but it didn't work, although this time it did install properly as opposed to Feisty. I'm still not getting video in skype, even though it recognizes the camera and the built-in mic works.

---

### Post by fragos on 2007-11-17
Much webcam software assumes a device address of /dev/video0.  In a terminal window do "ls /dev/video*" and see if there is a /dev/video1 or others.  One of those will be your webcam.  TV cards also mount as this class of video device.

---

### Post by Lothas on 2007-11-18
Nope, the output for ls /dev/video* is ```
/dev/video0
```

---

### Post by fragos on 2007-11-18
Try Applications-> Internet-> Ekiga and see if it works there.  That will tell you if the problem is specific to Skype.  I have no knowledge of Skype.

---

### Post by Lothas on 2007-11-18
Ekiga doesn't show video either. It recognizes the camera (I checked under preferences) but I get no input. I tried switching from PAL to AUTO but the Ekiga crashed and now it won't start (haven't tried restarting yet). Anyway, the problem is not Skype specific.

---

### Post by Lothas on 2007-11-26
Are there any news on my webcam issue? How do I know who wrote the driver for Gutsy? (it wasn´t available for Feisty)

---

### Post by fragos on 2007-11-27
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) works for me.

---

### Post by Lothas on 2007-11-27
Thanks fragos but I´ve visited that site before. I found this website:
[http://www.quickcamteam.net/]("http://www.quickcamteam.net/")
And found my camera there. Now I´m checking out the Quickcam express driver for my camera which should work ok:
[http://qce-ga.sourceforge.net/]("http://qce-ga.sourceforge.net/")

The thing is that up to feisty, I didn´t get anything from my camera other than a lsusb line but with gutsy, the camera is recognized and I can get audio from it. I was trying to figure out what kind of driver was added for Gutsy or if there was a bug fixed so that the built-in microphone works. Maybe I could take it from there and solve the video issue.

---

### Post by Lothas on 2007-12-09
I talked to the guys at qce-ga but didn't get much luck. They are working on a new version of the driver but when I tried to install it, it just messed up whatever I had working from the camera. Now I'm running skype and MSN from my VirtualBox Windows :(

---

### Post by mr_boo1711 on 2007-12-19
Ok - I'm having problems like everyone else.  I reckon I'm doing the basics wrong to be honest - probably cause I've been messing about with stuff prior to finding the [http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html") link.

Now I really think I need to remove any partial drivers files etc that I may have left in Linux but dont know how or what the best way would be?!?

Its a Logitech STX Camera

lsusb =

Bus 004 Device 002: ID 046d:08d7 Logitech, Inc.

And currently if I try to compile the file from the above link using the 'read me', this is the output....

steve@steve-desktop:~/Desktop/Camera/gspcav1-20071214$ sudo ./gspca_build 
 REMOVE the old module if present
ERROR: Module gspca is in use

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
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/steve/Desktop/Camera/gspcav1-20071214 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/steve/Desktop/Camera/gspcav1-20071214/gspca_core.o
  CC [M]  /home/steve/Desktop/Camera/gspcav1-20071214/decoder/gspcadecoder.o
  LD [M]  /home/steve/Desktop/Camera/gspcav1-20071214/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/steve/Desktop/Camera/gspcav1-20071214/gspca.mod.o
  LD [M]  /home/steve/Desktop/Camera/gspcav1-20071214/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

If you try and use the camera through camorama or AMSN it just says "Could not connect to video device (/dev/video0)  Please check connection." - I've had this same error message from the day I plugged the damn thing in out the box before I messed about with anything and its never changed! :(

Anyone any ideas?? (If more info is needed, just point me in the right direction and I'll supply it)

Cheers,
Steve

Using 7.10 Gutsy; 2.6.22.14-generic

---

### Post by fragos on 2007-12-19
First let's determine if there any other video class device.  In a terminal window do "ls /dev/video*.  Per chance do you have a video1 as well as video0?  There is a bug where when video class devices are assigned mount points they don't always come out in the same order.  If that's the case, we can fix it with a udev rule.  Some web cam applications will search for the web cam and other hard coded the mount points.  Also it appears that you compiled the driver while there was a web cam plugged in.  I don't know if that makes a difference but unpluing the USB cam before compiling might help.

---

### Post by mr_boo1711 on 2007-12-20
> **fragos said:**
> First let's determine if there any other video class device.  In a terminal window do "ls /dev/video*.  Per chance do you have a video1 as well as video0?  There is a bug where when video class devices are assigned mount points they don't always come out in the same order.  If that's the case, we can fix it with a udev rule.  Some web cam applications will search for the web cam and other hard coded the mount points.  Also it appears that you compiled the driver while there was a web cam plugged in.  I don't know if that makes a difference but unpluing the USB cam before compiling might help.

Hi Fragos,

Ok - I checked for more than one video class device...

steve@steve-desktop:~$ ls /dev/video*
/dev/video0
steve@steve-desktop:~$ 

Looks like thats a no go. :(

I also tried compiling it with the camera unplugged but got the same Ouput (Exactly the same).  So frsustrating!

I did consider that maybe another USB device was causing the problem (Maybe acting as a video device when it wasnt?!?).  The reason I suggest this is because there were 2 or 3 occassions about 7 months ago where I DID get it to work and the only thing I did at the time was plug/unplug USB devices and do random reboots. (Of course - the problem with that was that I couldnt trace the winning combination that resulted in the web cam finally working! lol)

I'll post my full lsusb if that helps... l (to follow on additional post)

---

### Post by mr_boo1711 on 2007-12-20
You wont believe this......  I've sorted it (Sort of)

(I better explain just in case it helps anyone else)

It seems I was right.  I had to reboot before posting this post, but before I did that I unplugged all by USB devices except my Logitech Edge Keyboard (Connects Via USB BT Dongle).  When I booted up I plugged in the cam FIRST and ran camoram... It worked first time. :) :) :KS   I then plugged in my External USB Freecom HD.. that worked ok.  and finally I plugged in the Cradle/Charging station for my MX900 Logitech mouse.... and it DIDNT work, although the lights came on etc.  Noe I'm thinking it may be something to do with the fact that technically I had 2 BT dongles plugged in (?!) - One for the mouse and one for the keyboard.

Regardless - I got it working. (I paired my Mouse to the logitech Edge dongle instead and hey-presto! - Only problem is charging it once every so often)

Thanks or all your help though Fragos.

---

### Post by fragos on 2007-12-20
I had some silmilar experience.  There are limits on the amount of 5 volt power that is available for USB device powering.  This is determined by the power supply.  My web cam wouldn't work when plugged into a powered hub.  There may be more power from the PC than availble with from the powered hub.  I now only plug my web cam into the PC directly.  To make ports available I moved all the low powered stuff to the hub.

---

### Post by mr_boo1711 on 2007-12-24
Ok I'm a tad annoyed - I thought I had sorted this. :(

It seems that when the PC is booted with the USB cam plugged in then it doesnt work, and when you unplug it and put it back in you still get this same error msg that i've been getting - Could not connect to video device (dev/video0) Please check connection.

IF the PC is booted WITHOUT plugging in the cam and then its plugged in when you're on the desktop enviroment - THEN it works ok.

Very strange..

Anyone??  Does the issue maybe lie within the USB ports as opposed to the Cam maybe?? :confused:

---

### Post by fragos on 2007-12-24
The only thing I can think of is to write a UDEV rule to create a mount point specific to your webcam.  I went back through the this thread and found your results from lsusb which I needed to write the rule.  Please note, I'm not relacing the the normal video mount point.  I'm creating an additional mount point for your webcam only.  Create a file /etc/udev/rules.d/95-perso.rules and insert the following line:

KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x08d7", SYMLINK+="video/webcam"

This new mount point is /dev/video/webcam.  You may need to restart to get this to take effect.  In a terminal window enter "ls /dev/video*" and you should now see the new webcam mount point.  Go to whatever application you are using and change the camera mount point.

---

### Post by kamaboko on 2008-03-09
> **amhirsch said:**
> I looked around and found: [http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)   

Which in looking at the date is newer than the gspca-20060925.tar.gz file that many people are using.

Download this file, uncompress it, change directories into gspca-20060930/gspcav1, and run the gspca_build script.  This popped my Logitech QuickCam Notebook Deluxe up right away. 

My usb info for the QuickCam is:  046d:08d8

I hope this helps others!

;)

How do you build the script?

---

### Post by fragos on 2008-03-09
Why not use the the latestest version?

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

---

### Post by kamaboko on 2008-03-09
> **fragos said:**
> Why not use the the latestest version?

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

OK, I just downloaded that and ran "sudo ./gspca_build" and it apparently installed everything.  So what do I do next?  Oh, and I have installed the latest aMSN.

---

### Post by fragos on 2008-03-09
Now you need to run an application that uses the web cam, Ekiga for example which was installed withj the default system.

---

### Post by kamaboko on 2008-03-09
OK, I think I've got this thing going.  I installed aMSN and was able to get an image.  :)

---

### Post by MarkCarras on 2008-03-10
Ok, I think I understand about ten percent of everything that has been posted on this.  

Still trying to get my Ubuntu to notice my webcam is plugged into the USB.  I had someone I know through Mixx.com explain the directions for EasyCam and got that installed and running, but it didn't make Ubuntu recognize the Webcam.  

So can someone give me a very dumbed down explanation as to what I should do next?  I'm not a total noob, but you people are talking way over my head right now. :confused:

I'm pretty sure I am using the latest version of Gutsy Gibbon and the camera is the STX Logitech.  Thanks in advance to anyone with enough patience to help me with this.

---

### Post by fragos on 2008-03-10
The web cam driver that comes with Ubuntu should work for you -- step 1.  Now you need an application that uses the web cam.  Lastly that application may need to be configured for your web cam mount point.  Without getting into details, if you have multiple video devices, as in web cam and TV card, your mount point may change between boots.  Likely you only have the web cam and your mount point will be /dev/video0.  The Ekiga Softphone, installed by default, can be used to see if the web cam works.

---

### Post by MarkCarras on 2008-03-13
I tried to get that program to work and it doesn't even seem to be able to finish opening.  Not sure what it does, but it doesn't want to open.  It got to the part where you test audio and everything is so quiet you could hear a pin drop. 

Arrgg!  Do I have to spend a few months trying to get this program to do something just to get my webcam to work?  Or is there an easier way?  This is getting extremely frustrating.

---

### Post by LinuX-M@n1@k on 2008-04-07
**@MarkCarras**
> **MarkCarras said:**
> I tried to get that program to work and it doesn't even seem to be able to finish opening.  Not sure what it does, but it doesn't want to open.  It got to the part where you test audio and everything is so quiet you could hear a pin drop. 

Arrgg!  Do I have to spend a few months trying to get this program to do something just to get my webcam to work?  Or is there an easier way?  This is getting extremely frustrating.
If you want you can also try "camorama" or "skype 2.0.0.68"
I had to wait 5-6 minutes until ekiga started ( I don't know why ), but when it started, for the first time ( since I deleted Windows ) I saw my face on the screen =D

**@fragos**
> **fragos said:**
> Why not use the the latestest version?

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
I own you a beer :lolflag: THANKS!!

PS: First you have to reboot, then test the webcam !

---

### Post by Krischu on 2008-05-28
I bought a Logitech Quickcam Deluxe for Notebooks recently and was hoping to get it working under Ubuntu 6.06 (dapper). I downloaded  [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz"), compiled it along with spcagui20060127, and finally, the camera is not being recognized, although it is listed in supported devices.

I found out that the USB ID is different and applied the following change
to [COLOR="SeaGreen"]**gspca_core.c**[/COLOR] :

```


[SIZE="1"]# diff gspca_core.c.orig  gspca_core.c
762c762
<       {USB_DEVICE(0x046d, 0x08a9)},   /* Logitech Notebook Deluxe */
---
>       {USB_DEVICE(0x046d, 0x09c1)},   /* Logitech Notebook Deluxe */
3385c3385
<               case 0x08a9:
---
>               case 0x09c1:

```
as a quick hack.

This leads to the camera being processed by the driver, but the driver bails out later when it finds an UNKNOW_0 sensor, forcing a Tas5130 and ending up in a DEALLOC error:

```

May 28 09:13:26 localhost kernel: [19668077.452000] usb 1-2: new full speed USB device using uhci_hcd and address 13
May 28 09:13:27 localhost kernel: [19668077.796000] /root/gspcav1-20071224/gspca_core.c: USB GSPCA camera found.(ZC3XX)
May 28 09:13:27 localhost kernel: [19668077.796000] /root/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG
May 28 09:13:27 localhost kernel: [19668078.540000] /root/gspcav1-20071224/Vimicro/zc3xx.h: [zc3xx_config:597]  Sensor UNKNOW_0 force Tas5130
May 28 09:13:28 localhost kernel: [19668078.544000] /root/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 160 minh 120
May 28 09:14:00 localhost kernel: [19668111.084000] /root/gspcav1-20071224/gspca_core.c: [spca5xx_open:1996]  DEALLOC error on init_Isoc
May 28 09:14:00 localhost kernel: [19668111.084000][/SIZE]




```

Any clues how to get this working?

---

