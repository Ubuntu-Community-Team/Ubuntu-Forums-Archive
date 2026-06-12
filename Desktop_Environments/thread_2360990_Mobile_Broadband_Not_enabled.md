---
title: "Mobile Broadband Not enabled"
date: 2017-05-10
forum: Desktop Environments
---

### Post by scojopa on 2017-05-10
Can anyone help here. I cannot get this working for the life of me. 
16.04.2 x64
 4.8.0-51-generic cat /
Lenovo T460S

In NetworkMgr Mobile Broadband is listed as "not enabled?

**Rfkill list all**
1: tpacpi_wwan_sw:Wireless WAN
	Soft blocked: no
	Hard blocked: no


**lshw** &#8594; notlisted


**lsusb** &#8594; Bus001 Device 020: ID 1199:9079 Sierra Wireless, Inc. 


dmesg &#8594; grep cdc
[    4.481691]usbcore: registered new interface driver cdc_ncm
[    4.496647]usbcore: registered new interface driver cdc_wdm
[    4.533827]cdc_mbim 1-2:1.12: cdc-wdm0: USB WDM device
[    4.533973]cdc_mbim 1-2:1.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-2,CDC MBIM, ca:63:73:1b:6b:51
[    4.534029]usbcore: registered new interface driver cdc_mbim
[    4.535325]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 2567.618415]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 2579.213913]cdc_mbim 1-2:1.12: cdc-wdm0: USB WDM device
[ 2579.216121]cdc_mbim 1-2:1.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-2,CDC MBIM, ca:63:73:1b:6b:51
[ 2579.266299]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 6322.812016]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 6334.546306]cdc_mbim 1-2:1.12: cdc-wdm1: USB WDM device
[ 6334.546533]cdc_mbim 1-2:1.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-2,CDC MBIM, ca:63:73:1b:6b:51
[ 6334.566334]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 8510.614165]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 8522.583872]cdc_mbim 1-2:1.12: cdc-wdm1: USB WDM device
[ 8522.584889]cdc_mbim 1-2:1.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-2,CDC MBIM, ca:63:73:1b:6b:51
[ 8522.622445]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0


dmegs &#8594; grep wwp
[    4.535325]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 2567.618415]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 2579.266299]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 6322.812016]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 6334.566334]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0
[ 8510.614165]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: unregister 'cdc_mbim'usb-0000:00:14.0-2, CDC MBIM
[ 8522.622445]cdc_mbim 1-2:1.12 wwp0s20f0u2i12: renamed from wwan0


**/var/lib/NetworkManager/NetworkManager.state**
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

