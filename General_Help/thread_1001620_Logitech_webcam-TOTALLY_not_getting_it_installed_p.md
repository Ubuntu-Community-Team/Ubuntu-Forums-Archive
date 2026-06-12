---
title: "Logitech webcam-TOTALLY not getting it installed properly"
date: 2008-12-04
forum: General Help
---

### Post by smartsmokey on 2008-12-04
sup folks, i have a problem like this poor soul - 
[http://ge.ubuntuforums.com/showthread.php?t=905086](http://ge.ubuntuforums.com/showthread.php?t=905086)
I got to the "type lsusb in terminal" thing, and did that and got this - 
Bus 003 Device 002: ID 046d:089d Logitech, Inc
okay so that's the webcam. Now what do I do? The thread I pasted above seems to teeter out after the lsusb results. Anyone have the sympathy to post some helpful links or instructions? 
   I was new to Ubuntu about 6 months ago...had never heard of it, installed it, and never looked back. I was actually able to get EVERYTHING on my Thinkpad to work...wi-fi, fingerprint reader, you name it. Took some work though. Anyway, now I have the webcam to drive me into insanity. Anyone have any ideas? :guitar:

---

### Post by smartsmokey on 2008-12-04
Buuuump

---

### Post by smartsmokey on 2008-12-04
following the directions in the link i posted above, here's what i get - 
smartsmokey@smartsmokey-laptop:~/gspcav1-20071224$ sudo rm /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko
rm: cannot remove `/lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko': No such file or directory

---

### Post by smartsmokey on 2008-12-05
bump

---

### Post by smartsmokey on 2008-12-07
bump

---

### Post by smartsmokey on 2008-12-15
bump

Seems support for things such as mouses and webcams with Ubuntu is like...talking to yourself!

---

### Post by kyphi on 2008-12-15
The 089d identifies the Logitech Quickcam Connect which is one of the very few Logitech webcams not guaranteed to work in Ubuntu.

There is a driver (gspcav1) which may work available here:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Installation is quite simple.
Download the driver file gspcav1-20071224.tar.gz
Best to put the downloaded file into a folder to work on.
Double click the file which will unpack the tarball and create a new folder called gspcav1-20071224.  Open that folder and click on "Extract".
Open a terminal and change directory to your newly-created folder.  If you created a folder in your Home directory and called it WebCam then in a terminal window type:
```
cd WebCam
```
Then type:
```
sudo ./gspca_build
```

This will install the gspca driver.

If your camera does not work with this driver you will have to buy another webcam.  I can recommend the Logitech Quickcam Pro 9000.

---

### Post by kyphi on 2008-12-16
This URL is a dud: [http://ge.ubuntuforums.com/showthread.php?t=905086](http://ge.ubuntuforums.com/showthread.php?t=905086)

It should read:  [http://ubuntuforums.org/showthread.php?t=905086](http://ubuntuforums.org/showthread.php?t=905086)

---

### Post by smartsmokey on 2008-12-17
hey hyphi. yeah i went through the thread you posted on the bottom before...didn't have luck. I got to some point in the install where it just failed to keep going. Also, there's a link to a page where a guy figured it out - but towards the bottom with comments you can see people saying "hey this doesn't work - any help? what's this file here?" and there's like NO replies. AHHHHH! Anyway thanks for the help, I'll look it over again

---

### Post by smartsmokey on 2008-12-17
downloaded the .tar.gz, unpacked it fine, didn't find an "extract" file, only "read and install." Checked that out and got confused so went back to your directions with cd webcam (or whatever i saved the file as - which was web camera actually), but when I type cd web camera nothing happens, command not found. So going back to the long thread again. This really stinks.

---

### Post by smartsmokey on 2008-12-17
results of commmand "lsusb" -
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 0a5c:2110 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:089d Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
the Logitech, Inc entry is the camera. So.....

---

### Post by smartsmokey on 2008-12-17
when i hit alt+f2 and type gstreamer-properties and go to video and detect, i get this
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

---

### Post by smartsmokey on 2008-12-17
typed "sudo udevmonitor --environment | tee video-udev.log" and got this - 

UEVENT[1229558221.766891] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1 (usb)
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1
SUBSYSTEM=usb
MAJOR=189
MINOR=259
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/003/004
PRODUCT=46d/89d/100
TYPE=0/0/0
BUSNUM=003
DEVNUM=004
SEQNUM=2966

UDEV  [1229558221.768803] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep82 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep82
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=24
SEQNUM=2956
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.4_ep82

UDEV  [1229558221.770361] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/004
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=255/255/255
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00icFFiscFFipFF
SEQNUM=2957
UDEVD_EVENT=1

UDEV  [1229558221.771638] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1 (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1
SUBSYSTEM=sound
MAJOR=14
MINOR=16
SEQNUM=2958
UDEVD_EVENT=1
DEVNAME=/dev/mixer1

UDEV  [1229558221.773010] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1 (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1
SUBSYSTEM=sound
MAJOR=14
MINOR=19
SEQNUM=2959
UDEVD_EVENT=1
DEVNAME=/dev/dsp1

UDEV  [1229558221.774196] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1 (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1
SUBSYSTEM=sound
MAJOR=14
MINOR=20
SEQNUM=2960
UDEVD_EVENT=1
DEVNAME=/dev/audio1

UDEV  [1229558221.775398] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c
SUBSYSTEM=sound
MAJOR=116
MINOR=56
SEQNUM=2961
UDEVD_EVENT=1
DEVNAME=/dev/snd/pcmC1D0c

UDEV  [1229558221.776576] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1 (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1
SUBSYSTEM=sound
MAJOR=116
MINOR=32
SEQNUM=2962
UDEVD_EVENT=1
DEVNAME=/dev/snd/controlC1

UDEV  [1229558221.777701] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/004
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/1/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc01ip00
SEQNUM=2963
UDEVD_EVENT=1

UDEV  [1229558221.785849] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/004
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/2/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc02ip00
SEQNUM=2964
UDEVD_EVENT=1

UDEV  [1229558221.787622] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.4_ep00
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=22
SEQNUM=2965
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.4_ep00

UDEV  [1229558221.792834] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1
SUBSYSTEM=usb
MAJOR=189
MINOR=259
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/003/004
PRODUCT=46d/89d/100
TYPE=0/0/0
BUSNUM=003
DEVNUM=004
SEQNUM=2966
UDEVD_EVENT=1
DEVNAME=/dev/bus/usb/003/004

UEVENT[1229558221.833609] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1 (sound)
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1
SUBSYSTEM=sound
SEQNUM=2967

UDEV  [1229558221.834557] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1 (sound)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1
SUBSYSTEM=sound
SEQNUM=2967
UDEVD_EVENT=1

UEVENT[1229558246.641901] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1
SUBSYSTEM=usb
MAJOR=189
MINOR=260
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
BUSNUM=003
DEVNUM=005
SEQNUM=2968

UEVENT[1229558246.642512] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.5_ep00 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.5_ep00
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=22
SEQNUM=2969

UDEV  [1229558246.644366] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1
SUBSYSTEM=usb
MAJOR=189
MINOR=260
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
BUSNUM=003
DEVNUM=005
SEQNUM=2968
UDEVD_EVENT=1
DEVNAME=/dev/bus/usb/003/005

UDEV  [1229558246.652861] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.5_ep00 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/usb_endpoint/usbdev3.5_ep00
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=22
SEQNUM=2969
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.5_ep00

UEVENT[1229558246.652909] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=23
SEQNUM=2971

UEVENT[1229558246.652925] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep82 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep82
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=24
SEQNUM=2972

UEVENT[1229558246.652938] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/1/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc01ip00
SEQNUM=2973

UEVENT[1229558246.666953] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1 (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1
SUBSYSTEM=sound
SEQNUM=2974

UEVENT[1229558246.666986] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c
SUBSYSTEM=sound
MAJOR=116
MINOR=56
SEQNUM=2975

UEVENT[1229558246.667001] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1 (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1
SUBSYSTEM=sound
MAJOR=14
MINOR=19
SEQNUM=2976

UEVENT[1229558246.667015] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1 (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1
SUBSYSTEM=sound
MAJOR=14
MINOR=20
SEQNUM=2977

UEVENT[1229558246.667038] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1 (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1
SUBSYSTEM=sound
MAJOR=116
MINOR=32
SEQNUM=2978

UEVENT[1229558246.667177] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1 (sound)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1
SUBSYSTEM=sound
MAJOR=14
MINOR=16
SEQNUM=2979

UEVENT[1229558246.670583] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2
SUBSYSTEM=usb
DEVTYPE=usb_interface
DRIVER=snd-usb-audio
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/2/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc02ip00
SEQNUM=2980

UDEV  [1229558246.768719] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=255/255/255
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00icFFiscFFipFF
SEQNUM=2970
UDEVD_EVENT=1

UDEV  [1229558246.770755] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=23
SEQNUM=2971
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.5_ep81

UDEV  [1229558246.771036] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2
SUBSYSTEM=usb
DEVTYPE=usb_interface
DRIVER=snd-usb-audio
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/2/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc02ip00
SEQNUM=2980
UDEVD_EVENT=1

UDEV  [1229558246.781221] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/003/005
PRODUCT=46d/89d/100
TYPE=0/0/0
INTERFACE=1/1/0
MODALIAS=usb:v046Dp089Dd0100dc00dsc00dp00ic01isc01ip00
SEQNUM=2973
UDEVD_EVENT=1

UDEV  [1229558246.781256] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep82 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep82
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=24
SEQNUM=2972
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.5_ep82

UDEV  [1229558246.781266] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1 (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1
SUBSYSTEM=sound
SEQNUM=2974
UDEVD_EVENT=1

UDEV  [1229558246.781275] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/pcmC1D0c
SUBSYSTEM=sound
MAJOR=116
MINOR=56
SEQNUM=2975
UDEVD_EVENT=1
DEVNAME=/dev/snd/pcmC1D0c

UDEV  [1229558246.781286] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1 (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/dsp1
SUBSYSTEM=sound
MAJOR=14
MINOR=19
SEQNUM=2976
UDEVD_EVENT=1
DEVNAME=/dev/dsp1

UDEV  [1229558246.781295] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1 (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/audio1
SUBSYSTEM=sound
MAJOR=14
MINOR=20
SEQNUM=2977
UDEVD_EVENT=1
DEVNAME=/dev/audio1

UDEV  [1229558246.784134] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1 (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/mixer1
SUBSYSTEM=sound
MAJOR=14
MINOR=16
SEQNUM=2979
UDEVD_EVENT=1
DEVNAME=/dev/mixer1

UDEV  [1229558246.785346] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1 (sound)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1/controlC1
SUBSYSTEM=sound
MAJOR=116
MINOR=32
SEQNUM=2978
UDEVD_EVENT=1
DEVNAME=/dev/snd/controlC1

UEVENT[1229558247.404971] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2/usb_endpoint/usbdev3.5_ep83 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2/usb_endpoint/usbdev3.5_ep83
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=25
SEQNUM=2981

UDEV  [1229558247.407428] add      /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2/usb_endpoint/usbdev3.5_ep83 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.2/usb_endpoint/usbdev3.5_ep83
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=25
SEQNUM=2981
UDEVD_EVENT=1
DEVNAME=/dev/usbdev3.5_ep83

UEVENT[1229558248.417000] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.

---

### Post by smartsmokey on 2008-12-17
so I'm disconnecting my cam and getting this-
UEVENT[1229558478.743115] remove   /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1 (sound)
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.1/sound/card1
SUBSYSTEM=sound
SEQNUM=2995

UDEV  [1229558478.743929] remove   /devices/pci0000:00/0000:00:1d.2/usb3

---

### Post by smartsmokey on 2008-12-17
gstreamer properties still getting this when i test input for linux sources- 
/dev/video0" does not exist

---

### Post by smartsmokey on 2008-12-17
okay trying actionshrimps faux factsand here's what goes down - 
smartsmokey@smartsmokey-laptop:~$ sudo modprobe -v gspca
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/media/video/v4l2-common.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.24-19-generic/ubuntu/media/gspcav1/gspca.ko 
smartsmokey@smartsmokey-laptop:~$ sudo rmmod fspca
ERROR: Module fspca does not exist in /proc/modules
smartsmokey@smartsmokey-laptop:~$ sudo rmmod gspca
smartsmokey@smartsmokey-laptop:~$ sudo rm  /lib/modules/2.6.24-19-generic/ubuntu/media/gspcav1/gspca.ko
smartsmokey@smartsmokey-laptop:~$ sudo /lib/modules/2.6.24-19-generic/ubuntu/media/gspcav1/gspca.ko
sudo: /lib/modules/2.6.24-19-generic/ubuntu/media/gspcav1/gspca.ko: command not found
smartsmokey@smartsmokey-laptop:~$ ls/dev/video*
bash: ls/dev/video*: No such file or directory
smartsmokey@smartsmokey-laptop:~$ ls dev/video*
ls: cannot access dev/video*: No such file or directory
smartsmokey@smartsmokey-laptop:~$ wget [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
--22:03:17--  [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
           => `gspcav1-20071224.tar.gz.4'
Resolving mxhaard.free.fr... 212.27.63.150
Connecting to mxhaard.free.fr|212.27.63.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 214,717 (210K) [application/x-gzip]

100%[====================================>] 214,717      275.84K/s             

22:03:18 (275.02 KB/s) - `gspcav1-20071224.tar.gz.4' saved [214717/214717]

smartsmokey@smartsmokey-laptop:~$ wget [http://forums.quickcamteam.net/attachment.php?aid=86](http://forums.quickcamteam.net/attachment.php?aid=86) -O patch.tar.gz
--22:03:31--  [http://forums.quickcamteam.net/attachment.php?aid=86](http://forums.quickcamteam.net/attachment.php?aid=86)
           => `patch.tar.gz'
Resolving forums.quickcamteam.net... 67.17.145.36
Connecting to forums.quickcamteam.net|67.17.145.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 784 [application/x-gzip]

100%[====================================>] 784           --.--K/s             

22:03:32 (69.51 MB/s) - `patch.tar.gz' saved [784/784]

smartsmokey@smartsmokey-laptop:~$ tar -xvf gspcav1-20071224.tar.gz
gspcav1-20071224/
gspcav1-20071224/decoder/
gspcav1-20071224/decoder/gspcadecoder.c
gspcav1-20071224/decoder/gspcadecoder.h
gspcav1-20071224/decoder/gspcadecoder-OSX.c
gspcav1-20071224/decoder/gspcadecoder-OSX.h
gspcav1-20071224/Makefile
gspcav1-20071224/Vimicro/
gspcav1-20071224/Vimicro/vc032x_sensor.h
gspcav1-20071224/Vimicro/zc3xx.h
gspcav1-20071224/Vimicro/cs2102.h
gspcav1-20071224/Vimicro/vc032x.h
gspcav1-20071224/Vimicro/pas106b.h
gspcav1-20071224/Vimicro/icm105a.h
gspcav1-20071224/Vimicro/hv7131b.h
gspcav1-20071224/Vimicro/hv7131c.h
gspcav1-20071224/Vimicro/pb0330.h
gspcav1-20071224/Vimicro/ov7630c.h
gspcav1-20071224/Vimicro/mc501cb.h
gspcav1-20071224/Vimicro/tas5130c_vf0250.h
gspcav1-20071224/Vimicro/ov7620.h
gspcav1-20071224/Vimicro/tas5130c.h
gspcav1-20071224/Vimicro/hdcs2020.h
gspcav1-20071224/Etoms/
gspcav1-20071224/Etoms/et61xx51.h
gspcav1-20071224/Sonix/
gspcav1-20071224/Sonix/sn9cxxx.h
gspcav1-20071224/Sonix/sonix.h
gspcav1-20071224/utils/
gspcav1-20071224/utils/spcagamma.h
gspcav1-20071224/utils/spcausb.h
gspcav1-20071224/utils/spcaCompat.h
gspcav1-20071224/Conexant/
gspcav1-20071224/Conexant/cx11646.h
gspcav1-20071224/Conexant/cxlib.h
gspcav1-20071224/Pixart/
gspcav1-20071224/Pixart/pac207-OSX.h
gspcav1-20071224/Pixart/pac7311.h
gspcav1-20071224/Pixart/pac207.h
gspcav1-20071224/changelog
gspcav1-20071224/license
gspcav1-20071224/gspca_core.c
gspcav1-20071224/Transvision/
gspcav1-20071224/Transvision/tv8532.h
gspcav1-20071224/Makefile.kld
gspcav1-20071224/gspca.h
gspcav1-20071224/Sunplus/
gspcav1-20071224/Sunplus/spca501.dat
gspcav1-20071224/Sunplus/spca505.dat
gspcav1-20071224/Sunplus/spca508.dat
gspcav1-20071224/Sunplus/spca561-OSX.h
gspcav1-20071224/Sunplus/spca506.h
gspcav1-20071224/Sunplus/spca561.h
gspcav1-20071224/Sunplus/spca501_init.h
gspcav1-20071224/Sunplus/spca508_init-OSX.h
gspcav1-20071224/Sunplus/spca508_init.h
gspcav1-20071224/Sunplus/spca501_init-OSX.h
gspcav1-20071224/Sunplus/spca505_init.h
gspcav1-20071224/Sunplus-jpeg/
gspcav1-20071224/Sunplus-jpeg/spca500.dat
gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20071224/Sunplus-jpeg/spca500_init.h
gspcav1-20071224/gspca_build
gspcav1-20071224/READ_AND_INSTALL
gspcav1-20071224/Mars-Semi/
gspcav1-20071224/Mars-Semi/mr97311.h
gspcav1-20071224/cutlog.py
smartsmokey@smartsmokey-laptop:~$ tar -xvf patch.tar.gz
quickcamE2500.diff
smartsmokey@smartsmokey-laptop:~$ cd gspcav1-20071224
smartsmokey@smartsmokey-laptop:~/gspcav1-20071224$ patch -p1 < ../quickcamE2500.diff
patching file gspca_core.c
smartsmokey@smartsmokey-laptop:~/gspcav1-20071224$ sudo ./gspca_build

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
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/smartsmokey/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/smartsmokey/gspcav1-20071224/gspca_core.o
  CC [M]  /home/smartsmokey/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /home/smartsmokey/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/smartsmokey/gspcav1-20071224/gspca.mod.o
  LD [M]  /home/smartsmokey/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
smartsmokey@smartsmokey-laptop:~/gspcav1-20071224$ smartsmokey
bash: smartsmokey: command not found
smartsmokey@smartsmokey-laptop:~/gspcav1-20071224$ cd
smartsmokey@smartsmokey-laptop:~$ lsmod | grep gspca
gspca                 680784  0 
videodev               29440  1 gspca
usbcore               146028  7 gspca,hci_usb,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
smartsmokey@smartsmokey-laptop:~$ sudo rmmod gspca
smartsmokey@smartsmokey-laptop:~$ sudo modprobe -v gspca
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/gspca.ko 
smartsmokey@smartsmokey-laptop:~$ sudo rmmod gspca
smartsmokey@smartsmokey-laptop:~$ sudo /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/gspca.ko
sudo: /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/gspca.ko: command not found
smartsmokey@smartsmokey-laptop:~$ sudo rmmod gspca
ERROR: Module gspca does not exist in /proc/modules
smartsmokey@smartsmokey-laptop:~$ sudo rmmod gspca
ERROR: Module gspca does not exist in /proc/modules
smartsmokey@smartsmokey-laptop:~$ gspca
bash: gspca: command not found
smartsmokey@smartsmokey-laptop:~$ sudo  /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/gspca.ko
sudo: /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/gspca.ko: command not found
smartsmokey@smartsmokey-laptop:~$ 

I also noticed that in actionshrimps tutorial it reads "/lib/modules/2.624-20"<<<<<<<not like here where it's "/lib/modules/2.264-19" Hmm. This is driving me crazy.

---

### Post by Snow986 on 2008-12-17
What version of ubuntu are you using?  If its not 8.10, upgrading may help. Seems like some compatability issues have been fixed in 8.10.  If not its just a shot in the dark. I have a logitech quickcam and it works out of the box in 8.10.  Good Luck!

---

### Post by smartsmokey on 2008-12-17
well got it working in cheese somehow! Only thing is that after a minute or two the brightness drops dramatically and you can't see me. I think there's a patch for that somewhere.

---

### Post by cariboo on 2008-12-17
You didn't mention what version of Ubuntu you are using, but my Logitech Quickcam Messanger needed the driver from [here]("http://mxhaard.free.fr/spca5xx.html"), but since Intrepid, it works out of the box. It won't work in cheese or canorama, but will work in xawtv if I use this command:

```
xawtv -c /dev/video1
```

and it works in egika without doing anything. In my case the webcam is /dev/video1 because my tvtuner card is /dev/video0

Jim

---

### Post by smartsmokey on 2008-12-17
> **Snow986 said:**
> What version of ubuntu are you using?  If its not 8.10, upgrading may help. Seems like some compatability issues have been fixed in 8.10.  If not its just a shot in the dark. I have a logitech quickcam and it works out of the box in 8.10.  Good Luck!

hey snow. Yeah I'm still using 8.04. I'm weary of upgrading, as the computer now seems so unstable...it's perfect and probably on the brink of collapse....just look what i went through for a webcam - imagine what I did to my registry and files when I added the biometric reader and compiz fusion. I still can't find the article about adjusting the brightness - people were saying it was too dark, and they did some etc/darkness/expo1 or something. Any ideas? Anyone?

---

### Post by smartsmokey on 2008-12-17
> **cariboo907 said:**
> You didn't mention what version of Ubuntu you are using, but my Logitech Quickcam Messanger needed the driver from [here]("http://mxhaard.free.fr/spca5xx.html"), but since Intrepid, it works out of the box. It won't work in cheese or canorama, but will work in xawtv if I use this command:

```
xawtv -c /dev/video1
```

and it works in egika without doing anything. In my case the webcam is /dev/video1 because my tvtuner card is /dev/video0

Jim

cariboo it actually works in cheese for me...but it's way to dark. Is nice and bright for maybe a minute, then goes pretty dark. Trying to find the code to fix that.

---

### Post by smartsmokey on 2008-12-18
so it's too dark, and "actionshrimp" says 
 The gspca driver itself can take options, and an autoexposure setting was ruining my lighting. To fix this, edit the file /etc/modprobe.d/options, and add a line at the bottom:

options gspca gamma=1 autoexpo=0

The gamma=1 may not be necessary, but if it still appears too dark or too light for your taste you can change this parameter as you like. Finally, reload the module:

sudo rmmod gspca
sudo modprobe gspca
I typed /etc/modprobe.d/options and it said "command not found." Wait now it says "Bash: permission denied," but when i type it in again and follow up with my password I get TA DA!!! - "command not found"

---

### Post by Jose Catre-Vandis on 2008-12-18
```
sudo nano /etc/modprobe.d/options
```

---

### Post by smartsmokey on 2008-12-18
Jose so I got this - 
               Modified  

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

The instructions said to add the "options gspca gamma=1 autoexpo=0"
to the bottom...but the bottom of which set of data? The top one or the bottom one?

---

### Post by smartsmokey on 2008-12-18
doing the above seemed to increase my brightness, thankfully. Though, it needs more light...so which fields do I increase or decrease to achieve this? 
   Also, I failed to mentioned that the audio on my laptop has failed to continue functioning due to all of the programming and screwing with it.

---

### Post by smartsmokey on 2008-12-19
Now the webcam will not work at all, Cheese won't even see it now. This is a serious issue. I am now burning a copy of XP and installing that. For students and professionals that don't have the time or training for the multitude of problems that arise due to Ubuntu's instability, I strongly suggest using Ubuntu as an OS only in instances where you're using the computer strictly for word processing and wed-surfing. But even then, an enormous amount of Googling and copying and pasting and research is needed to get Flash or most other kinds of "supported" programs working. Thread closed: NOT solved

---

### Post by smartsmokey on 2008-12-20
well apparently the 50th time was the charm with Actionshrimp's tutorial. There's a point about half-way into it that goes into replacing the old module or driver or something...well I had been doing that, BUT - there never was an older module/driver present. So it wasn't installing. Did the command lines up to the point where you replace old module/driver, typed the ls- dev/video* thing and bam! just like that dev/video0 or whatever...all there. Works awesome. ONLY bad thing is when I go to stickam my video feed is HORRIBLE - picture is clean, but it's zoomed like into my EYE. From a good 4-feet away. And in Cheese it's just fine. So is there a way to de-zoom by adding a command line to the driver gspca or whatever, like in actionshrimp's page where he talks about adding commands at the end of etc/modprobe that say exp=0 rate=1 and stuff? If anyone has any thoughts please chime in, I've gotten SO far with this. I feel like a computer scientist or something...everything is working.Here's what was going on (the following command lines and instructions are from actionshrimp) - 
First, download the drivers and the patch

wget [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
wget [http://forums.quickcamteam.net/attachment.php?aid=86](http://forums.quickcamteam.net/attachment.php?aid=86) -O patch.tar.gz

Then extract and apply the patch:

tar -xvf gspcav1-20071224.tar.gz
tar -xvf patch.tar.gz
cd gspcav1-20071224
patch -p1 < ../quickcamE2500.diff

There&#8217;s a handy build script included with the drivers so just run that (requires root):

sudo ./gspca_build

This generates the file

gspca.ko

which we use to replace the old gspca module.
Check to see if the old module is loaded, you should see something like:

dave@baracus:~$ lsmod | grep gspca
gspca                 680656  0
videodev               29440  1 gspca
usbcore               146028  9 gspca,snd_usb_audio,snd_usb_lib,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd

We want to find out where it is, so do the following:

sudo rmmod gspca
sudo modprobe -v gspca

You should see something like:

insmod /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko

That is the location of the file we&#8217;re looking for, so, replacing where appropriate with what was output for you above, type:

sudo rmmod gspca
sudo rm /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/gspca.ko
sudo mv gspca.ko /lib/modules/2.6.24-20-generic/ubuntu/media/gspcav1/
sudo modprobe gspca

This should have loaded the new module in place of the old one. See if you have a video device:

dave@baracus:~$ ls /dev/video*
/dev/video0

After sudo /gspca-build created everything, I think I just went ahead and typed in -ls /dev/video0 to see if it worked, and the yellow letters came up saying dev/video0. Sorry I can't be of more help...I suck with computers...thankfully Ubuntu is a lot more user-friendly than other OS's

---

