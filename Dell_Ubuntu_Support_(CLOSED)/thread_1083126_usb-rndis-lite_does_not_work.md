---
title: "usb-rndis-lite does not work"
date: 2009-02-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by killerdragon on 2009-02-28
I recently purchased a Dell Mini 9 with Ubuntu 8.04 preinstalled on the computer. I went ahead and tried to get my laptop to sync up with my pda/cell phone (its a Windows Mobile phone) and everything I try to do does not work. I have a feeling this is due to the lpia architecture, but I do not know for sure. 
Basically, I tried many walkthroughs:
[http://ubuntuforums.org/showthread.php?t=1074090&highlight=usb-rndis-lite](http://ubuntuforums.org/showthread.php?t=1074090&highlight=usb-rndis-lite)
[http://ubuntuforums.org/showthread.php?t=869229&highlight=usb-rndis-lite+dell+mini](http://ubuntuforums.org/showthread.php?t=869229&highlight=usb-rndis-lite+dell+mini)
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
[http://onlyubuntu.blogspot.com/2008/08/how-to-connect-to-hsdpa3g-trough-usb.html](http://onlyubuntu.blogspot.com/2008/08/how-to-connect-to-hsdpa3g-trough-usb.html)

Each one comes up with the same results. The modules will compile but when I plugin my phone to get it to sync all I get in dmesg is:
[ 1019.627372] rndis_host: Unknown symbol usbnet_cdc_unbind
[ 1074.084899] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 1074.254383] usb 4-2: configuration #1 chosen from 1 choice
[ 1074.385484] usbnet: exports duplicate symbol usbnet_resume (owned by kernel)
[ 1074.393260] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 1074.393277] cdc_ether: Unknown symbol usbnet_get_endpoints
[ 1074.399538] rndis_host: disagrees about version of symbol usbnet_skb_return
[ 1074.399554] rndis_host: Unknown symbol usbnet_skb_return
[ 1074.400118] rndis_host: Unknown symbol usbnet_generic_cdc_bind
[ 1074.400422] rndis_host: Unknown symbol usbnet_cdc_unbind

sudo modprobe rndis_host yields:
WARNING: Error inserting usbnet (/lib/modules/2.6.24-19-lpia/usb-rndis/usbnet.ko): Invalid module format
WARNING: Error inserting cdc_ether (/lib/modules/2.6.24-19-lpia/usb-rndis/cdc_ether.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rndis_host (/lib/modules/2.6.24-19-lpia/usb-rndis/rndis_host.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Anyone have any ideas? As I am sure other people will be or are having the same issues.

---

