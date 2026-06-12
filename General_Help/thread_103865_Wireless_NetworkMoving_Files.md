---
title: "Wireless Network/Moving Files"
date: 2005-12-14
forum: General Help
---

### Post by jmhickman09 on 2005-12-14
I just installed 5.10 and I like it. But my wireless network doesn't work. It didn't work on 5.04 either. I have a dell "external" usb wireless card, would that be a problem? It does recognize the wireless card, but the internet does not work. I really don't know much about the wireless stuff.

On another topic, I want to move over my files from my windows partition. Is that possible, and what is the easiest way? (40gig HD, 34gig partition for windows, approx. 6gig for ubuntu) 

Thanks.

---

### Post by jmhickman09 on 2005-12-14
Alright I read this post ([http://www.ubuntuforums.org/showthread.php?t=85182](http://www.ubuntuforums.org/showthread.php?t=85182)) and it's a little over my head but it sounds like it might work right? Still need help on the internet stuff tho.

---

### Post by redactech on 2005-12-14
Please give us the exact model number of your wireless card and revision (if it has)

then we do some console kung fu and give us the result for each command :

lsusb

iwconfig 

cat /etc/network/interfaces

then we'll go ahead (btw the link you provide us is not about wireless but about sharing fat32 partition)

---

### Post by zoiks on 2005-12-15
[QUOTE=jmhickman09]On another topic, I want to move over my files from my windows partition. Is that possible, and what is the easiest way? (40gig HD, 34gig partition for windows, approx. 6gig for ubuntu) 

Thanks.[/QUOTE]

If you just want to copy some files, it's easy for ubuntu to read (but not write, if it's NTFS-formatted) from the windows partition.  But if you need more space, resizing the partitions is a different matter.  Check out "gparted" for messing around with the partitions, but be careful since you can hose your data quickly.  Make backups of your data or transfer the files first to a network shared folder.

FWIW I would stay far, far away from VCOM "Partition Commander".  It advertises the ability to resize linux filesystems such as reiserfs, but it hosed mine twice (this was a year ago).  Fortunately I had copied the entire drive before futzing with it.  Got my money back from Fry's for that P.O.S. program.  The NTFS partition resize worked, sorta, but WIndows bitched a few times after doing so.  (Horrors! : Partition Commander boots up Caldera DR DOS! :( Run away run away! )

---

### Post by jmhickman09 on 2005-12-15
My wireless adapter is a Dell Wireless 1450 Wireless USB Adapter model: D145OU




ok for the things you told me to type:

When I typed lsusb:

[B]Bus 004 Device 003: ID 413c:8104 Dell Computer Corp.
Bus 004 Device 002: ID 046e:3002 Behavior Tech. Computer Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/B]



when I typed iwconfig:
[B]

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/B]



when I typed cat /etc/network/interfaces:

[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
[/B]



Just curious... If i wanted to have a partition that would work well with both windows and ubuntu what filesystem should it be? And how would I make one? (I need to resize the ntfs partition)

I tried the Gparted thing but what do I do once I have the folder in Ubuntu ? extract or something?

---

### Post by jmhickman09 on 2005-12-15
aargh...

---

### Post by Lambert on 2005-12-15
Do this.

1. run this command

sudo lshw -businfo

look for the device in the list and notice what the class is then run

sudo lshw -C class

replace class with the class of the device you found in the first command

2. rerun lsusb but add -v to the end of the command and post that output here.

lsusb -v

wireless is a challenge in linux at times, hang in there, this will take a few posts.

do you have your cd with the windows drivers?

---

### Post by jmhickman09 on 2005-12-15
I do have the windows cd. Thanks for responding. I'll try the commands. BRB

---

### Post by jmhickman09 on 2005-12-15
alrite messed up brb again

---

### Post by jmhickman09 on 2005-12-15
user@ubuntuJMH:~$ sudo lshw -businfo
Bus info      Device       Class       Description
==================================================
                           system      Dimension 3000
                           bus         0TC667
                           memory      BIOS
cpu@0                      processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
                           memory      L1 cache
                           memory      L2 cache
                           processor   Logical CPU
                           processor   Logical CPU
                           memory      System Memory
                           memory      DIMM SDRAM Synchronous 400 MHz (2.5 ns)
                           memory      DIMM SDRAM Synchronous 400 MHz (2.5 ns)
pci@00:00.0                bridge      82865G/PE/P DRAM Controller/Host-Hub Interface
pci@00:02.0                display     82865G Integrated Graphics Controller
pci@00:1d.0                bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
usb@1         usb1         bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
pci@00:1d.1                bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
usb@2         usb2         bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
usb@2:1                    input       DELL USB Keyboard
usb@2:2                    input       Microsoft Wireless Optical Mouse
pci@00:1d.3                bus         82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
usb@3         usb3         bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
pci@00:1d.7                bus         82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
usb@4         usb4         bus         Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
usb@4:1       scsi0        storage     USB 2.0 Storage Device
scsi@0.0:0.0  /dev/cdrom1  disk        USB5216
usb@4:2                    generic     Dell Wireless 1450 Dual-band (802.11a/b/g) USB 2.0 Adapter
usb@4:8       scsi1        storage     JUMPDRIVE
scsi@1.0:0.0  /dev/sda     disk        JUMPDRIVE
pci@00:1e.0                bridge      82801 PCI Bridge
pci@01:08.0   eth0         network     82562EZ 10/100 Ethernet Controller
pci@00:1f.0                bridge      82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
pci@00:1f.1                storage     82801EB/ER (ICH5/ICH5R) IDE Controller
ide@0         ide0         bus         IDE Channel 0
ide@0.0       /dev/hda     disk        ST340014A
ide@1         ide1         bus         IDE Channel 1
ide@1.0       /dev/hdc     disk        GCR-8485B
pci@00:1f.3                bus         82801EB/ER (ICH5/ICH5R) SMBus Controller
pci@00:1f.5                multimedia  82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
user@ubuntuJMH:~$ sudo lshw -C generic
  *-usb:1 UNCLAIMED
       description: Generic USB device
       product: Dell Wireless 1450 Dual-band (802.11a/b/g) USB 2.0 Adapter
       vendor: DELL
       physical id: 2
       bus info: usb@4:2
       version: 10.50
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=480.0MB/s


AND WHEN I TYPED IN THE lsusb -v IT TOOK UP TOO MUCH SPACE I GUESS? I THINK THAT PART OF THIS GOT CUT OUT OR SOMETHING. HERE IS WHAT WAS IN THE WINDOW AFTER I TYPED IT:

 bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 004 Device 003: ID 413c:8104 Dell Computer Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8104
  bcdDevice           10.50
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 004 Device 002: ID 046e:3002 Behavior Tech. Computer Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x046e Behavior Tech. Computer Corp.
  idProduct          0x3002
  bcdDevice            1.03
  iManufacturer           0
  iProduct                1
  iSerial                 2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValu

---

### Post by Lambert on 2005-12-15
Not everything is there but with this and some searching it looks like you need to use an app called ndiswrapper. It basically makes the windows drivers for your device work in linux.

There's a link in my signature for ndiswrapper. Go there and follow the instructions.

The main wiki page for ndiswrapper is at the bottom of that page if you need more help.

In the link it says make sure to use the correct driver and walks through a process to find the correct driver. For your device you'll find it points to the drivers on your disk. So just use those. Just make sure you copy all files to your drive from the xp file. Should be a .inf and .sys file and possibly a .bin file.

Post back if you have problems and somebody might help you or I'll be back around tomorrow.

---

### Post by jmhickman09 on 2005-12-16
thanks for your help lambert, i have the DELLNIC.inf file showing up in the gtdisk windows network thing (Administration-Windows...) and it says hardware:yes. However, what do I do now? (BTW the $ndiswrapper -l thing says command not found). Keep in mind, I have no clue how to configure anything or do anything like that for the network. When i went to the configure network thing, all that it showed were ethernet and modem connections.

---

### Post by jmhickman09 on 2005-12-17
Alright thanks everyone I got the internet working and I'm writing this from ubuntu.

---

