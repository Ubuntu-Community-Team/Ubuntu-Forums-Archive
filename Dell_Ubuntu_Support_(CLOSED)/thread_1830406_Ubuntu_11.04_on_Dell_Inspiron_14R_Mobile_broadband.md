---
title: "Ubuntu 11.04 on Dell Inspiron 14R Mobile broadband problem"
date: 2011-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rocket16 on 2011-08-21
Hello respected members.

I've been using Ubuntu for a long time (around 2 years) and am really impressed by it. I bought a new Dell Inspiron 14R last week and erased the default windowws installation, replacing it with ubuntu 11.04 (Classic environment).

For internet, I use a mobile broadband connection from an USB stick (Tata Photon plus, India). Previously it worked very well on my old compaq laptop. But now, while trying it out on the new one, I am facing huge problems.

First, the network manager applet shows 'Mobile broadband not enabled' even after I've enabled it many times. It is getting connected though, but the speed is very less and it gets disconnected very often. I am sure it works flawlessly on other computers. 

Second, I thought there might be a problem regarding USB 3.0 which my laptop makes use of. But as I read, ubuntu (linux) supports USB 3.0 very well. So, I guess the USB modem is not facing any problem because of that.

Here are my usb-devices output:
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4500 Rev=01.00
S:  Manufacturer=Broadcom
S:  Product=BCM2046B1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=94mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=03 Prnt=03 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=8161 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=01 Lev=03 Prnt=03 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=8162 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)

T:  Bus=01 Lev=03 Prnt=03 Port=02 Cnt=03 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=413c ProdID=8160 Rev=01.73
S:  Manufacturer=Dell Computer Corp
S:  Product=Dell Wireless 365 Bluetooth Module
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=641d Rev=9a.07
S:  Manufacturer=CN0FJT7K724870C5A77PA00
S:  Product=Laptop_Integrated_Webcam_1.3M
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0138 Rev=38.82
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20090516388200000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#= 12 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=140b Rev=00.00
S:  Manufacturer=HUAÿWEI TECHNOLOGIES
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

And here is my lsusb output:
```
Bus 002 Device 012: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The modem is from Huaywei technologies. 

The towers are functional too, and I am worrying this might be a computer problem. Any help will be really welcome, and thanks in advance.

---

### Post by nandan079 on 2011-12-02
i too have the same laptop and using tata photon plus huawie device with my ubuntu, it works perfectly fine on my machine...

why don't u use the tata photon+ linux software bundled along with the device.

i used the same software and it works fine.
but make sure to install tjat software as root. else it won't work.

---

