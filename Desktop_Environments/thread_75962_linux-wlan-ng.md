---
title: "linux-wlan-ng"
date: 2005-10-14
forum: Desktop Environments
---

### Post by BIS on 2005-10-14
Hallo All, 

New to this list. 

Been using hoary for a while, and getting ready to do the complete move over from XP to breezy. However...

Before I do that, I need to get my wireless lan working. Its a Philips CPWBS054/00, based on the prism2 chipset. I have read that I will probably need the linux-wlan-ng drivers. But...

Do any of you know of a good how-to? I mean I can apt-get install them, then what? Also, my wlan uses wpa. Any good links?

---

### Post by Dr. Nick on 2005-10-14
First off, If you want WPA and wlan-ng drivers I think your out of luck :( I never saw how to set it up, dont think its suported yet, Someone correct me If im wrong... please let me be wrong I want it too :)

Is it a usb,pcmcia, or pci card it makes a little bit of difference.

[ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README)

Follow only parts of that, not sure which to follow for pci or pcmcia though. To bring up my USB prism2 card I use

modprobe prism2_usb
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem(or sharedkey for wep)

Ill post more help if needed but the forums seem messed up right now so posting for me is sorta hard :)

---

### Post by BIS on 2005-10-15
bummer - no wpa....

Anyway, thanks for replying :-) I will read through this. It's a usb dongle, hopefully I can get it working. Perhaps I will need to write my own how-to...

---

### Post by az on 2005-10-15
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

---

### Post by az on 2005-10-15
To get my prism2_usb device working, I need to install linux-wlan-ng (using synaptic-  it is on the cd) and then configure my connection by hand
by running a script which I copy into /etc/hotplug/usb/prism2_usb:


(Save this as prism2_usb)
_____________



wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0

wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="(mysecretWEPkey)"

wlanctl-ng wlan0 lnxreq_autojoin ssid="(myssid)" authtype="sharedkey"

sleep 2

dhclient wlan0



_____________
(Change the (mysecretWEPkey) to whatever your WEP is  Ex:


wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="445566aabb"

---

### Post by Dr. Nick on 2005-10-15
That may help me a bit to azz, my way is sorta crude and involves modifying the interfaces file for each new network, then running those commands in a terminal. Hooray for bash history :) Have you set up a wlan-ng file for each network like suggested in the readme? I dont run the 
```
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true

wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0

wlanctl-ng wlan0 dot11req_mibset
mibattribute=dot11WEPDefaultKey0="(mysecretWEPkey) "
``` 

Instead I have files called wlancfg-"each ssid" with those strings set for each AP so I only do the ifstate=enable and join ssid commands.

I am going to read through that bug report and see if any is helpfull to me and may see if it can be summarized some. I can get my setup working its just a crude way to do it :KS

---

