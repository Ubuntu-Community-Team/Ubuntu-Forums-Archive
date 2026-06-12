---
title: "Error in obexftp -b 00:1F:00:B1:1C:C4 -l"
date: 2009-02-26
forum: General Help
---

### Post by gireesh_m on 2009-02-26
Dear All,
I am using BlueZ-4.18 and obexftp.
by using these i am trying to connect my linux system with mobile phone via bluetooth.

the steps i have done are given below

[root@localhost apps]# hcitool scan
Scanning ...
        00:1F:00:B1:1C:C4       Shams
[root@localhost apps]# sdptool browse 00:1F:00:B1:1C:C4
Browsing 00:1F:00:B1:1C:C4 ...
Service Name: AVRCP Target
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10000
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x10015
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: Headset Audio Gateway
Service RecHandle: 0x10016
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x10042
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AVRCP Controller
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10043
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: SyncMLClient
Service RecHandle: 0x10044
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10045
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 11
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Nokia OBEX PC Suite Services
Service RecHandle: 0x10046
Service Class ID List:
  UUID 128: 00005005-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005005-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: SyncML DM Client
Service RecHandle: 0x10047
Service Class ID List:
  UUID 128: 00000004-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000004-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: Nokia SyncML Server
Service RecHandle: 0x10049
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 14
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: SIM Access
Service RecHandle: 0x1004a
Service Class ID List:
  "SIM Access" (0x112d)
  "Generic Telephony" (0x1204)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "SIM Access" (0x112d)
    Version: 0x0101

Service RecHandle: 0x1004b
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3

Service Name: OBEX Object Push
Service RecHandle: 0x1004c
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: Dial-Up Networking
Service RecHandle: 0x1004d
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Imaging
Service RecHandle: 0x1004e
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 15
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100[root@localhost apps]# hcitool info 00:1F:00:B1:1C:C4
Requesting information ...
        BD Address:  00:1F:00:B1:1C:C4
        Device Name: Shams
        LMP Version: 2.0 (0x3) LMP Subversion: 0x6cc
        Manufacturer: Cambridge Silicon Radio (10)
        Features: 0xbf 0xee 0x0f 0x46 0x98 0x19 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset> 
                <timing accuracy> <role switch> <sniff mode> <RSSI> 
                <channel quality> <SCO link> <HV3 packets> <u-law log> 
                <A-law log> <CVSD> <paging scheme> <power control> 
                <transparent SCO> <EDR ACL 2 Mbps> <EDR ACL 3 Mbps> 
                <inquiry with RSSI> <AFH cap. slave> <AFH class. slave> 
                <3-slot EDR ACL> <5-slot EDR ACL> <AFH cap. master> 
                <AFH class. master> 
[root@localhost apps]# ./obexftp -b 00:1F:00:B1:1C:C4 -l
Browsing 00:1F:00:B1:1C:C4 ...
Connecting...failed: connect
error on connect(): Success
Still trying to connect
Connecting...failed: connect
error on connect(): Success
Still trying to connect
Connecting...failed: connect
error on connect(): Success
Still trying to connect

I don't know why this error is coming....
If anyone knows the cause of this please help me....

thanks in advance

Regards,
Gireesh.M

---

### Post by chomski on 2009-02-26
I've replicated your problem, I get the same thing when I put in the wrong pincode in the phone when it asks for authentication.
Are you getting prompted for the auth code on the mobile?

---

### Post by gireesh_m on 2009-02-27
dear chomski,

i didn't get any auth prompt on my mobile

---

