---
title: "DLink DWL-122 WLAN Driver Compile"
date: 2005-10-31
forum: Desktop Environments
---

### Post by derekr44 on 2005-10-31
I am attempting to compile the linux-wlan-ng-0.2.2 drivers for my DLink DWL-122 USB wireless card.  It is asking me for the Linux Source Directory.  Any directory I enter, I get the following error:

Linux source tree /lib/modules/2.6.12-9-386/build is imcomplete or missing!
Configuration failed

Any help?  I just neet to get this wireless card working so I can get on the internet and run Synaptic.  My PC is about 200 feet from the wireless router, so running a cable is not an option :P

Where is the Linux Source Tree??? (PS, I am a newb and this is the first time I have ever compiled a driver on a Linux system)

---

### Post by derekr44 on 2005-11-01
<bump>

Anyone have any ideas?  Big roadblock from getting me to move to Ubuntu... :(

---

### Post by ultra.nj on 2005-11-01
try [this]("http://www.ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122")

---

### Post by derekr44 on 2005-11-01
Tried that and it looks like it installed ok.  But when I run the "sudo sh /etc/hotplug/usb/p80211" command, I get the following:

> sudo: wlanct1-ng: command not found
sudo: wlanct1-ng: command not found
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I eventually ran  3 cables and two switches to get the pc wired to the router and attempted to reinstall the driver via Synaptic, but it still doesn't work.

---

### Post by derekr44 on 2005-11-02
Ok, I got it to work doing the following:

> derek@ubuntu:$ modprobe p80211 prism2_doreset=1
derek@ubuntu:$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
derek@ubuntu:$ sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=****** authtype=opensystem
message=lnxreq_autojoin
  ssid='******'
  authtype=opensystem
  resultcode=success
derek@ubuntu:$ sudo ifconfig wlan0 192.168.1.102


It ran for about 2 minutes, then the device disappeared and was no longer available in System>Administration>Networking.

sudo sh sighhhhhhhhhh

---

### Post by derekr44 on 2005-11-03
Just a friendly bump.

Has anyone been able to get a DWL-122 working with ndiswrapper?

---

### Post by az on 2005-11-03
There is a bug report about this device.  It is apparently supposed to work out-of-the-box once you install linux-wlan-ng.  You should be able to set up your device and connect on boot with the networking Gnome GUI tool.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

What I need to do to get it to work is to put this script into /etc/hotplug/usb/prism2_usb

Being that that module is hotplug loaded, that script is run when it is plugged in.

Here it is:
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="####PUTYOURWEPHERE!!!!!###"
wlanctl-ng wlan0 lnxreq_autojoin ssid="###PUT you essid here###" authtype="sharedkey"
sleep 2
dhclient wlan0


(Put your wep where indicated...)

I have used this device for a while and it used to be flakey.  Even in windows, it only connects half the time.  However, using the prism2_usb driver and this script, it never fails.  It is an unelegant solution, but it works for me.


Add to the bug report, if it applies to you, please.

---

