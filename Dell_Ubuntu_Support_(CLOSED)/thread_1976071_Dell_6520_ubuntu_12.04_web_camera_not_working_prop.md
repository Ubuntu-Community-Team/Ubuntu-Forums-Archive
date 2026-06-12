---
title: "Dell 6520 ubuntu 12.04 web camera not working properly"
date: 2012-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aa-hcl on 2012-05-08
Hi,

I have got Dell 6520 and latest version of ubuntu 64bit 12.04 installed as upgraded from 11.10. The problem below was also present in 11.10, so it was not resolved by 12.04 as I hoped (I should say that several hardware-related problems were solved by 12.04  for me - i.e. USB3.0 support).

Problem:
web camera can only work in poor 640x480 resolution and it is not possible to change the settings through guvcview application. When I try to change the resolution to 1920x1080 or any other, even lower, resolution using guvcview, the guvcview crashed and when restarted it refused to show any picture at all. Only after system restart the initial 640x480 resolution is shown. Cheese webcam program shows the same low-res picture.

I tried to find out what camera I have using lsusb -v and I also tried to look what driver is used using lsmod - see the output of both commands below. From what it is printed by lsusb I guess the camera may be recognised properly, but I somehow need to change the settings of the driver.

How can I solve the problem and get proper resolution on my webcamera?

Please help! 

------------------

lsusb -v output related to the webcamera:


Bus 001 Device 003: ID 05ca:181c Ricoh Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x05ca Ricoh Co., Ltd
  idProduct          0x181c 
  bcdDevice           12.28
  iManufacturer           1 CN0CJ3P27248714M0D8GA01
  iProduct                2 Laptop_Integrated_Webcam_FHD
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         1008
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               4 Integrated Webcam
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              4 Integrated Webcam
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength          104
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          5
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00060004
          Auto-Exposure Priority
          Focus, Auto
          Privacy
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x1b
          None
          NTSC - 525/60
          SECAM - 625/50
          NTSC - 625/50
      VideoControl Interface Descriptor:
        bLength                27
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 3
        guidExtensionCode         {0a3e1874-8254-1a48-b402-48b8b8c49cc8}
        bNumControl            12
        bNrPins                 1
        baSourceID( 0)          2
        bControlSize            2
        bmControls( 0)       0xff
        bmControls( 1)       0xc3
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {c385b80f-c268-4745-90f7-8f47579d95fc}
        bNumControl             4
        bNrPins                 1
        baSourceID( 0)          3
        bControlSize            1
        bmControls( 0)       0x0f
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             5
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               4
        iTerminal               0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            15
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         2
        wTotalLength                      613
        bEndPointAddress                  130
        bmInfo                              1
        bTerminalLink                       5
        bStillCaptureMethod                 1
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
        bmaControls( 1)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                7
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x02
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            50
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 36864000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           1333333
      VideoStreaming Interface Descriptor:
        bLength                            50
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x01
          Still image supported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 12165120
        dwMaxBitRate                 48660480
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           1333333
      VideoStreaming Interface Descriptor:
        bLength                            50
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x01
          Still image supported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                  9216000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           1333333
      VideoStreaming Interface Descriptor:
        bLength                            50
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x01
          Still image supported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  3041280
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           1333333
      VideoStreaming Interface Descriptor:
        bLength                            50
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x01
          Still image supported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  2304000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  6
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            400000
        dwFrameInterval( 2)            500000
        dwFrameInterval( 3)            666666
        dwFrameInterval( 4)           1000000
        dwFrameInterval( 5)           1333333
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           1000000
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1920
        wHeight                          1080
        dwMinBitRate                165888000
        dwMaxBitRate                165888000
        dwMaxVideoFrameBufferSize     4147200
        dwDefaultFrameInterval        2000000
        bFrameIntervalType                  1
        dwFrameInterval( 0)           2000000
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        2
        bNumFrameDescriptors                7
        bFlags                              0
          Fixed-size samples: No
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x02
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                110592000
        dwMaxBitRate                221184000
        dwMaxVideoFrameBufferSize      921600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x01
          Still image supported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 36495360
        dwMaxBitRate                 72990720
        dwMaxVideoFrameBufferSize      304128
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x01
          Still image supported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 27648000
        dwMaxBitRate                 55296000
        dwMaxVideoFrameBufferSize      230400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x01
          Still image supported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                  9123840
        dwMaxBitRate                 18247680
        dwMaxVideoFrameBufferSize       76032
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x01
          Still image supported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  6912000
        dwMaxBitRate                 13824000
        dwMaxVideoFrameBufferSize       57600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                331776000
        dwMaxBitRate                663552000
        dwMaxVideoFrameBufferSize     2764800
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         7
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1920
        wHeight                          1080
        dwMinBitRate                746496000
        dwMaxBitRate                1492992000
        dwMaxVideoFrameBufferSize     6220800
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  2
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            666666
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0270  1x 624 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x02bc  1x 700 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0348  1x 840 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0bfc  2x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1278  3x 632 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1320  3x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x135c  3x 860 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       9
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13bc  3x 956 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      10
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13c0  3x 960 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      11
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13c8  3x 968 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      12
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13fc  3x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting      13
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
        ** UNRECOGNIZED:  24 ff 42 49 53 54 00 01 05 02 10 00 00 00 00 00 01 06 b8 0b 02 07 b8 0b 03 08 b8 0b 04 09 4e 20 05 0a b8 0b
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

--------------------------------------

lsmod output related to the camera:


aa@aa-i7:~$ lsmod
Module                  Size  Used by
....

uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev

....

---

### Post by aa-hcl on 2012-05-10
Hi,

here is the update. 

After some updates of ubuntu or for any other reason I was able to change the resolution in guvcview to 1920x1080 and change settings. However, it was possible ONLY:
1. After the reboot and using the guvcview for the first time since reboot
2. I can usually make only one or two changes to the settings (i.e. increase brightness) and then it usually stops responding.

I then decided to compare the webcamera performance on Ubuntu 12.04 and Win7 (I have kept the Win7 installed by Dell when the laptop was shipped).

The result is shocking:  under Windows using the Dell application I had similar problems as under linux - both problems as described above and even worse (the Dell webcamera application did not show any camera view at all when I tried to change the camera resolution and settings - after two or three attempts it stopped responding and showed only black window and I had to shut it down through task manager).

The picture quality under Win7 and Ubuntu 12.04 was the same and the problems very similar.

I therefore concluded that the above problems with the webcamera are due to hardware and not software (or Win7 and Ubuntu have the same driver!!!).

I tried to update the BIOS from version A04 to A12 fro my E6520, but it had no effect in ubuntu (I did not check in Win7).

In Summary - my solution is to use external logitech where the image quality is adjusted automatically (by hardware I guess) and the picture quality is much better.

The Dell internal Camera is either not good or it has not got a proper driver even for Win7  (or both) !!!

---

### Post by c169144 on 2012-05-15
Hey, mate
I've got Dell E5520 laptop with 12.04 clean install (beta2) and similar webcam:

**Bus 001 Device 004: ID 05ca:181e Ricoh Co., Ltd **

It's visible for programs as "Laptop_Integrated_Webcam_FHD"
I can switch between all resolutions in guvcview, but i'm not sure that quality of picture is really better at 1920x1080 than 640x480.

Could you check how your cam works in Skype? I use latest beta (2.2.0.35) and it seems it can't switch on "exposure control", because picture is very dark. The same effect has switching off that control in guvcview.

Also i would very appreciate any ideas how to make it work with normal picture.
(LD_PRELOAD things doesn't make any sense)

Thanks in advance

---

### Post by aa-hcl on 2012-05-16
**>>****Bus 001 Device 004: ID 05ca:181e Ricoh Co., Ltd **

my camera could be slightly different - it says 181c and not as yours "181e", but I guess it does not make any big difference.

>>>It's visible for programs as "Laptop_Integrated_Webcam_FHD"

Yes, the same for me - this is what you get as description of the device if you type "lsusb -v" and go to the camera section


>> I can switch between all resolutions in guvcview, but i'm not sure that quality of picture is >> really better at 1920x1080 than 640x480.

Now I can also switch between resolution. However, the 1920x1080 picture is as bad as low resolution. I checked this in Win7 with branded Dell camera software  (I have a dual-boot dell, but work mainly in ubuntu - win7 is kept for rare occasions) and it is no different from ubuntu - the picture is very bad.

>>> Could you check how your cam works in Skype? 

Actually my main use of camera is skype and that is why I want the camera to work better

>>> I use latest beta (2.2.0.35) and it seems it can't switch on "exposure control", because >>> picture is very dark. 

I am sorry for stupid question - but where did you find "exposure control" in skype of this version?

I have the same version of skype and I can not find anything like that. And yes - the picture is very dark!!!


I tried the following (once it worked, but then it stopped working):
In guvcview I put the brightness to maximum. The picture became not that dark as with default, dark, settings. I then tried to save that in guvcview, exit guvcview normally. Then in skype the picture also became lighter, but this worked only once, In all other occasions when I changed the brightness settings in guvcview, then the camera stopped responding at all and I can not use it in skype anymore. I have to reboot to get the camera working again.

Another strange behavior in skype: sometimes it starts with bad picture and then it changes to a better picture after sometime. However, this is not reproducible.

I must say that the same problems I had under Win7 - the camera stopped responding when I tried to change settings!!!!

i therefore think it is a bad camera as a hardware or the driver both for linux and win7 is not working properly. I tried to update all dell bios and other software, but it is still the same.

I therefore use external logitech270 which gives much better quality even when the room is dark!

---

### Post by aa-hcl on 2012-05-16
Here is my further updates, which probably solves the issue:

1. Restart the computer (relogin to gnome is not enough).
2. open guvcview and put the brightness to maximum. Close guvcview normally.
3. At that point skype and cheese will loose the camera and the camera is not available.
4. Restart the computer. After the restart the skype camera will be as bright as possible for this camera.

NOTE: do NOT open guvcview anymore at this point. My previous error was that being excited with positive result I tried to make it better and opened guvcview again for further tuning. I found that opening guvcview after the brightness is set and skype camera is working will make it stop working! Apparently when opened guvcview will automatically set the parameters to default and you need to do the list above again.

After the above procedure the camera view quality in skype in ubuntu and in skype in Win7 on the same dell are the same. I checked it by booting to ubuntu, then booting to Win7 and then to ubuntu again.  It is as bright as possible. It is a bad quality camera in dell 6520 compared to logitech270 that i have as external usb camera.

---

### Post by c169144 on 2012-05-16
> **aa-hcl said:**
> 
Now I can also switch between resolution. However, the 1920x1080 picture is as bad as low resolution. I checked this in Win7 with branded Dell camera software  (I have a dual-boot dell, but work mainly in ubuntu - win7 is kept for rare occasions) and it is no different from ubuntu - the picture is very bad.

The quality of the picture in 640x480 mode to my taste is sufficient for Skype. According to guvcview, when i switch camera into 1920x1080 mode frame rate becomes as low as 1 frame/sec (slideshow), so i believe in our case FHD is purely a marketing resolution.
> **aa-hcl said:**
> 
I am sorry for stupid question - but where did you find "exposure control" in skype of this version?

I have the same version of skype and I can not find anything like that. And yes - the picture is very dark!!!

I didn't say Skype has that control :)
1. Start guvcview, make sure picture is ok
2. Locate "Auto Exposure" (or something like that, i'm writing this from work - no access to my lappy atm) and turn it off.
3. Make screenshot
4. Start Skype and compare its picture with screenshot.
> **aa-hcl said:**
> 
I tried the following (once it worked, but then it stopped working):
In guvcview I put the brightness to maximum. The picture became not that dark as with default, dark, settings. I then tried to save that in guvcview, exit guvcview normally. Then in skype the picture also became lighter, but this worked only once, In all other occasions when I changed the brightness settings in guvcview, then the camera stopped responding at all and I can not use it in skype anymore. I have to reboot to get the camera working again.

Another strange behavior in skype: sometimes it starts with bad picture and then it changes to a better picture after sometime. However, this is not reproducible.

I must say that the same problems I had under Win7 - the camera stopped responding when I tried to change settings!!!!

i therefore think it is a bad camera as a hardware or the driver both for linux and win7 is not working properly. I tried to update all dell bios and other software, but it is still the same.

I therefore use external logitech270 which gives much better quality even when the room is dark!

I can't check my cam quality with Win7, because i deleted it immediately after getting laptop.
And once again - to my taste, the picture in default camera resolution (it seems it's 640x480 mode) in guvcview/cheese is very good.

---

### Post by aa-hcl on 2012-05-16
About the FHD:  
in my Dell 6520 the camera does work as full HD 1920x1080 with proper number of frames per second. 

The FHD 1920x1080 camera quality is fine, BUT only if the room is light enough. That was the main problem: it is not always the case the I skype in the room with perfect lighting! 

i just guess that low quality in poor lighting conditions can be more visible in FHD resolution.

In conclusion, I think that I just have to accept the fact that the camera on Dell 6520 is not as good as logitech and it is not an issue with ubuntu (after I tuned the camera setttings).

---

### Post by c169144 on 2012-05-17
> **aa-hcl said:**
> Here is my further updates, which probably solves the issue:

1. Restart the computer (relogin to gnome is not enough).
2. open guvcview and put the brightness to maximum. Close guvcview normally.
3. At that point skype and cheese will loose the camera and the camera is not available.
4. Restart the computer. After the restart the skype camera will be as bright as possible for this camera.

NOTE: do NOT open guvcview anymore at this point. My previous error was that being excited with positive result I tried to make it better and opened guvcview again for further tuning. I found that opening guvcview after the brightness is set and skype camera is working will make it stop working! Apparently when opened guvcview will automatically set the parameters to default and you need to do the list above again.

After the above procedure the camera view quality in skype in ubuntu and in skype in Win7 on the same dell are the same. I checked it by booting to ubuntu, then booting to Win7 and then to ubuntu again.  It is as bright as possible. It is a bad quality camera in dell 6520 compared to logitech270 that i have as external usb camera.
I completed your steps, mate.
At step 3) skype and cheese didn't lost camera, but picture in skype became whitish, staying in general bad and unacceptable for use.
At step 4) nothing has changed.

My 12.04 is 64bit, maybe yours is 32bit and it explains the difference in behaviour of our cams?

---

### Post by c169144 on 2012-05-17
> **aa-hcl said:**
> About the FHD:  
in my Dell 6520 the camera does work as full HD 1920x1080 with proper number of frames per second. 

The FHD 1920x1080 camera quality is fine, BUT only if the room is light enough. That was the main problem: it is not always the case the I skype in the room with perfect lighting! 

i just guess that low quality in poor lighting conditions can be more visible in FHD resolution.

In conclusion, I think that I just have to accept the fact that the camera on Dell 6520 is not as good as logitech and it is not an issue with ubuntu (after I tuned the camera setttings).
OK, mate, maybe guvcview displays wrong information about framerate or something else. I'd like to see real camera specs from Ricoh, to make conclusions.

---

### Post by aa-hcl on 2012-05-17
Hi,

I have just tested the camera by recording the video with 1920x1080 25frames/sec and it is fine. I am therefore sure that the webcamera on dell6520 can indeed do FHD video - the trouble is its very bad sensitivity at poor light.

The parameters of the camera is in the first post of the this thread - through typing "lsusb -v", but I do not know how to find and interpreter the resolution and frames per seconds capability - I can only see from that the set of parameters that can be tuned for the camera and that is what guvcview apparently is reading.

---

### Post by c169144 on 2012-05-17
> **aa-hcl said:**
> Hi,

I have just tested the camera by recording the video with 1920x1080 25frames/sec and it is fine. 
I'd like to test my cam. Is it possible to do that in Ubuntu?

---

### Post by aa-hcl on 2012-05-17
Hi,

I do not know how to test the camera in ubuntu, I just used cheese to record the video and then played in ubuntu and looked at the property of the video to see that it is FHD. the "cheese" can not set the frames per seconds, at least i could not find where to set it, so I just used the default cheese settings.

---

