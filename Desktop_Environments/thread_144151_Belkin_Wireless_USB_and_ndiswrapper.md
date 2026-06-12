---
title: "Belkin Wireless USB and ndiswrapper"
date: 2006-03-13
forum: Desktop Environments
---

### Post by thor2023 on 2006-03-13
I am trying to get my Belkin 54g USB Network Adapter to work with the Ubuntu livecd (this is the critical factor in whether or not I install Linux). A little bit of research indicates that ndiswrapper is the way to go. So, the story so far:


<puts the ndiswrapper package and the drives from windows on a USB stick>
<boots the livecd (ubuntu-5.10-live-i386.iso)>
<opens a terminal>

ubuntu@ubuntu:~$ sudo dpkg -i /media/USBDISKPRO/synapticcache/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 56801 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-4ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

ubuntu@ubuntu:~$ sudo ndiswrapper -i /media/USBDISKPRO/BelkinDrivers/rt73.inf
Installing rt73
ubuntu@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
rt73    driver present, hardware present
ubuntu@ubuntu:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
ubuntu@ubuntu:~$ sudo depmod -a
ubuntu@ubuntu:~$ sudo modprobe ndiswrapper

<blinking cursor>
<opens new terminal>

ubuntu@ubuntu:~$ dmesg

<snip>

[4295315.741000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4295315.974000] ndiswrapper: driver rt73 (Belkin,08/02/2005, 1.00.00.0000) loaded
[4295316.366000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[4295316.366000]  printing eip:
[4295316.366000] cf051ad3
[4295316.366000] *pde = 00000000
[4295316.366000] Oops: 0002 [#1]
[4295316.366000] Modules linked in: ndiswrapper nls_utf8 vfat fat rfcomm l2cap bluetooth ipv6 powernow_k7 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi i2c_acpi_ec hotkey dev_acpi container button battery ac pcspkr rtc snd_via82xx_modem snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_viapro i2c_core via_ircc irda crc_ccitt pci_hotplug via_agp agpgart joydev tsdev psmouse lp md dm_snapshot dm_mod loop cloop af_packet via_rhine mii nls_cp437 pcmcia sr_mod sbp2 isofs ide_cd cdrom ide_disk ide_floppy ide_generic pdc202xx_new aec62xx alim15x3 amd74xx atiixp cmd64x cs5520 cs5530 cy82c693 generic hpt34x ns87415 opti621 pdc202xx_old piix rz1000 sc1200 serverworks siimage sis5513 slc90e66 triflex trm290 floppy parport_pc parport sd_mod fbcon tileblit font bitblit vga16fb vgastate vesafb cfbcopyarea cfbimgblt cfbfillrect softcursor usbserial usbkbd thermal processor fan mousedev usb_storage scsi_mod usbhid via82cxxx ide_core ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 yenta_socket rsrc_nonstatic pcmcia_core evdev unix
[4295316.366000] CPU:    0
[4295316.366000] EIP:    0060:[<cf051ad3>]    Tainted: P      VLI
[4295316.366000] EFLAGS: 00010246   (2.6.12-9-386)
[4295316.366000] EIP is at 0xcf051ad3
[4295316.366000] eax: 00000000   ebx: c654f000   ecx: 00000000   edx: 00000000
[4295316.366000] esi: ffffffed   edi: c987f800   ebp: caa07d7c   esp: caa07d74
[4295316.366000] ds: 007b   es: 007b   ss: 0068
[4295316.366000] Process loadndisdriver (pid: 24049, threadinfo=caa06000 task=c38775e0)
[4295316.366000] Stack: 00000000 00000000 caa07dfc cf0501eb 00000000 0000000c c05ecca0 00000001
[4295316.366000]        ceff4aa7 00000000 00000000 00000000 cf0945b1 00000000 00000000 00000020
[4295316.366000]        cf094630 ffffffed 00000000 ceff779d cf094630 c654f220 c654f000 cf0521a4
[4295316.366000] Call Trace:
[4295316.366000]  [<ceff4aa7>] wrap_kmalloc+0x3d/0x78 [ndiswrapper]
[4295316.366000]  [<ceff779d>] NdisMInitializeTimer+0xf/0x2c [ndiswrapper]
[4295316.366000]  [<ceffce82>] miniport_init+0x57/0x5b [ndiswrapper]
[4295316.366000]  [<ceff3878>] ndiswrapper_add_one_usb_dev+0x8f/0x154 [ndiswrapper]
[4295316.366000]  [<ce8a904f>] usb_probe_interface+0x49/0x60 [usbcore]
[4295316.366000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4295316.366000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4295316.366000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4295316.366000]  [<c01ec7a5>] driver_register+0x23/0x25
[4295316.366000]  [<ce8a910d>] usb_register+0x42/0x87 [usbcore]
[4295316.366000]  [<ceff45e5>] register_devices+0x43a/0x4d2 [ndiswrapper]
[4295316.366000]  [<c014fd35>] link_path_walk+0x83/0xad
[4295316.366000]  [<c019cb84>] copy_from_user+0x34/0x58
[4295316.366000]  [<ceff46b3>] wrapper_ioctl+0x36/0xaa [ndiswrapper]
[4295316.366000]  [<c0152fd8>] do_ioctl+0x48/0x4e
[4295316.366000]  [<c0153233>] vfs_ioctl+0x172/0x17f
[4295316.366000]  [<c0153286>] sys_ioctl+0x46/0x60
[4295316.366000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4295316.366000] Code: fc 00 00 00 00 8b 45 08 89 45 f8 c7 45 fc 00 00 00 00 eb 09 8b 4d fc 83 c1 01 89 4d fc 8b 55 fc 3b 55 0c 73 0b 8b 45 f8 03 45 fc <c6> 00 00 eb e4 8b e5 5d c2 08 00 cc cc 55 8b ec 83 ec 0c 8b 45
[4295316.366000]  <3>ndiswrapper (wrapper_init:1534): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
[4295316.393000] usbcore: deregistering driver ndiswrapper


I guess the problem is in the bit where the kernel dereferences a null pointer :-? any ideas?
If this is a version problem and I have to compile newer ones then I'm a bit screwed, as installing gcc is easily enough to freeze the livecd, and I don't think I want to install an entire OS based on some random from the internet saying "it will probably work if you recompile your kernel"

---

### Post by Zelut on 2006-03-13
Unfortunately, from what I've heard, trying to load ndiswrapper & wireless on the  LiveCD is near impossible.

if you want to run a few commands for me & tell me the output I can tell you fairly definitely whether the card will work or not.  (I've got ndiswrapper working for wireless on a range of cards--VERY few have turned out unsupported.)

If you could tell me the output of:
lspci | grep 802.11
dmesg | 802.11
and also the output of
lspci -n

---

### Post by thor2023 on 2006-03-13
lspci | grep 802.11

Nothing

dmesg | grep 802.11

Nothing

lspci -n

0000:00:00.0 0600: 1106:3156
0000:00:01.0 0604: 1106:b091
0000:00:0a.0 0607: 1217:6972
0000:00:0c.0 0c00: 104c:8026
0000:00:10.0 0c03: 1106:3038 (rev 80)
0000:00:10.1 0c03: 1106:3038 (rev 80)
0000:00:10.3 0c03: 1106:3104 (rev 82)
0000:00:11.0 0601: 1106:3177
0000:00:11.1 0101: 1106:0571 (rev 06)
0000:00:11.5 0401: 1106:3059 (rev 50)
0000:00:11.6 0780: 1106:3068 (rev 80)
0000:00:12.0 0200: 1106:3065 (rev 74)
0000:01:00.0 0300: 5333:8d04

It looks like these questions are based on me having a pci card. Actually it is a USB adaptor pen thing.
So, using my initiative

lsusb

Bus 003 Device 006: ID 0d7d:1420 Phison Electronics Corp. PS2044 Pen Drive
Bus 003 Device 005: ID 0926:8888
Bus 003 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 003 Device 003: ID 050d:705a Belkin Components
Bus 003 Device 002: ID 050d:0217 Belkin Components
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by Zelut on 2006-03-13
Sorry, my bad.  Good thinkin'.

Can you also output 'sudo lsusb -v' (trying to find the right ID for the wireless to match with ndiswrapper)..

---

### Post by thor2023 on 2006-03-13
lsusb -v

Bus 003 Device 006: ID 0d7d:1420 Phison Electronics Corp. PS2044 Pen Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0d7d Phison Electronics Corp.
  idProduct          0x1420 PS2044 Pen Drive
  bcdDevice            0.02
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              200mA
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

Bus 003 Device 005: ID 0926:8888
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0926
  idProduct          0x8888
  bcdDevice            2.88
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      97
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

Bus 003 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x05fe Chic Technology Corp.
  idProduct          0x0011 Browser Mouse
  bcdDevice            0.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              5
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

Bus 003 Device 003: ID 050d:705a Belkin Components
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705a
  bcdDevice            0.01
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
    iConfiguration          4
    bmAttributes         0x80
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5
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
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 003 Device 002: ID 050d:0217 Belkin Components
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x0217
  bcdDevice            6.0b
  iManufacturer           0
  iProduct                0
  iSerial                 0
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
    MaxPower              100mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted

Bus 003 Device 001: ID 0000:0000
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

Bus 002 Device 001: ID 0000:0000
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
        bInterval             255
can't get hub descriptor: Operation not permitted

Bus 001 Device 001: ID 0000:0000
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
        bInterval             255
can't get hub descriptor: Operation not permitted


saw all the "not permitted"s and remembered to use sudo. and it hung the terminal, odd.

---

### Post by Zelut on 2006-03-13
What model is this Belkin card?

---

### Post by thor2023 on 2006-03-13
Wireless G USB Network Adapter

Part # F5D7050uk 

[http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=203472&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F](http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=203472&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F)

---

### Post by thor2023 on 2006-03-15
I am typing this from the Dapper Drake livecd, which comes with ndiswrapper 1.8 :D Thanks for your help.

---

