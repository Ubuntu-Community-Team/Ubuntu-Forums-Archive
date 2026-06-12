---
title: "webcam drivers"
date: 2008-06-21
forum: Florida Team - US
---

### Post by wayne972 on 2008-06-21
I have a veo webcam built for windows applications. How do I get the drivers needed to get it to work on Ubuntu????:(

Any help will be appreciated :)

Just got my Ubuntu installed and downloaded the 8.0 version. It's a big difference from my old Mangrove but just as powerful if not more. 

Also where is a sercurity website for Ubuntu I can go to. I want to learn how to close ports on Linux.

---

### Post by mlsquad on 2008-06-22
> **wayne972 said:**
> I have a veo webcam built for windows applications. How do I get the drivers needed to get it to work on Ubuntu????:(

Any help will be appreciated :)

Just got my Ubuntu installed and downloaded the 8.0 version. It's a big difference from my old Mangrove but just as powerful if not more. 

Also where is a sercurity website for Ubuntu I can go to. I want to learn how to close ports on Linux.

Have you tried Ubuntu yet?  Most hardware that works with Ubuntu will just work out of the box.  You probably won't have to do anything.  If you have not installed it yet, download the ISO and boot up to the live CD and see if it works in the live environment.
Ubuntu has all ports closed by default.  You don't actually have to do anything to close ports.  You only have to open ports manually as needed.  Most programs, such as SSH and VNC will open the ports for you on install and close them on upon uninstall.

---

### Post by linuxwizard on 2008-06-22
wayne972
Alot of webcams will just work. Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by mlsquad on 2008-06-22
[http://ubuntuforums.org/showthread.php?t=40893](http://ubuntuforums.org/showthread.php?t=40893)
The above thread may be of some use for you.

---

### Post by wayne972 on 2008-07-04
Sorry it took so long to reply...
 I went to Ubunto home site and found nada there. I went through Ekiga but that didn't work either. Im wondering how new 8.04 is? Maybe it;s still a lil querky. I am also having a hard time opening .exe files and there is nothing in my archiver to open them. Anyone out there with the same problem.
:popcorn: thanks for your help

Wayne

---

### Post by Quicksilver_Johny on 2008-07-06
I also have a Veo Stingray webcam, which I cannot seem to get working.
```
qj@ubuntu:~$ sudo lsusb -vd 0545:800c

Bus 001 Device 005: ID 0545:800c Xirlink, Inc. Veo StingRay
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x0545 Xirlink, Inc.
  idProduct          0x800c Veo StingRay
  bcdDevice            3.0a
  iManufacturer           0 
  iProduct                1 USB IMAGING DEVICE
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03fe  1x 1022 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03fe  1x 1022 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

```
 
> **wayne972 said:**
> Sorry it took so long to reply...
 I went to Ubunto home site and found nada there. I went through Ekiga but that didn't work either. Im wondering how new 8.04 is? Maybe it;s still a lil querky. I am also having a hard time opening .exe files and there is nothing in my archiver to open them. Anyone out there with the same problem.
:popcorn: thanks for your help

Wayne

8.04 was released 24/04/08, hence 8.04.
Ubuntu uses [.deb]("http://en.wikipedia.org/wiki/.deb") Debian packages. You can find most software via Synaptic (System>Administration>Synaptic Package Manager), or "Add/Remove" (Application>Add/Remove), however, for random programs found on webpages, look for .deb files or tar.gz/bz2 source archives, from which you can compile the code, Usually by ```
./configure
make
sudo make install
``` but read the README and INSTALL files.

You can find most cross-platform Free and Open Source Software (Firefox, pidgin, GIMP, Audacity, etc.) in Synaptic, or get a .deb online, or the source code, but if you *must* have windows-only programs, you can run [wine]("http://en.wikipedia.org/wiki/Wine_(software)"), a Microsoft Windows emulator. Install by running
```
sudo apt-get install wine
```.

:)

---

