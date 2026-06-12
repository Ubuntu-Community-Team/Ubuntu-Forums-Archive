---
title: "Dell Inspiron 1525 - Webcam not detected/no driver installed"
date: 2011-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Koushik Sarkar on 2011-06-12
Hi,

I have recently installed Ubuntu 11.04 on my Dell Inspiron 1525 removing MS Windows Vista. It is working absolutely fine except 1 issue: it has not detected my webcam or it hasn't installed the driver for the same.
Can any one please help me to make my webcam working on Ubuntu?

Thanks in advance,

Koushik sarkar

---

### Post by webofunni on 2011-06-12
are you able to see the device in 

```

sudo lsusb -v

```

---

### Post by Koushik Sarkar on 2011-06-12
Yes, it is there... plz find the details as below....

  	 	 	 	 	 	  Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam  
 Device Descriptor:  
   bLength                18  
   bDescriptorType         1  
   bcdUSB               2.00  
   bDeviceClass          239 Miscellaneous Device  
   bDeviceSubClass         2 ?  
   bDeviceProtocol         1 Interface Association  
   bMaxPacketSize0        64  
   idVendor           0x05a9 OmniVision Technologies, Inc.  
   idProduct          0x2640 OV2640 Webcam  
   bcdDevice            1.00  
   iManufacturer           1 OmniVision Technologies, Inc. -2640-07.07.20.3  
   iProduct                2 Laptop Integrated Webcam  
   iSerial                 0  
   bNumConfigurations      1  
   Configuration Descriptor:  
     bLength                 9  
     bDescriptorType         2  
     wTotalLength          705  
     bNumInterfaces          2  
     bConfigurationValue     1  
     iConfiguration          0  
     bmAttributes         0x80  
       (Bus Powered)  
     MaxPower              500mA  
     Interface Association:  
       bLength                 8  
       bDescriptorType        11  
       bFirstInterface         0  
       bInterfaceCount         2  
       bFunctionClass         14 Video  
       bFunctionSubClass       3 Video Interface Collection  
       bFunctionProtocol       0  
       iFunction               2 Laptop Integrated Webcam  
     Interface Descriptor:  
       bLength                 9  
       bDescriptorType         4  
       bInterfaceNumber        0  
       bAlternateSetting       0  
       bNumEndpoints           1  
       bInterfaceClass        14 Video  
       bInterfaceSubClass      1 Video Control  
       bInterfaceProtocol      0  
       iInterface              2 Laptop Integrated Webcam

---

### Post by webofunni on 2011-06-12
what 

```

sudo ls -l /dev/video*
sudo lsmod | grep -i video

```

says

---

