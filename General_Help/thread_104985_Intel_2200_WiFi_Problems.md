---
title: "Intel 2200 WiFi Problems"
date: 2005-12-17
forum: General Help
---

### Post by lkdhiri on 2005-12-17
Hi,

I am trying to get my Samsung R50's Intel 2200 WiFi running with Ubuntu 5.10. Unfortunately I am stuck, though, I am sure the WiFi settings are right I can not get a working internet connection using DHCP or static IP. No signal is being sent and received.

General setup
128 Key (ASCII) WEP
Intel 2200 WiFi (shows as eth1)
Thomson SpeedTouch 716g ADSL Router
Currently configed using static IPs and am posting this msg using eth0 (Broadcom Ethernet)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel= 0  Access Point: 00:00:00:00:00:00
          Bit Rate= 0 kb/s   Tx-Power= 20 dBm
          Retry limit: 7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

sit0      no wireless extensions.

I have looked at other WiFi problem posts with 5.10 but not managed to solve the problem based on information found there. Any help appreciated.

TIA

Lalit

---

### Post by joaquimperez on 2005-12-22
try  iwconfig eth0 essid default ap 00:11:22:33:44

where  'default'  and  '00:11:22:33:44' are an example of values, you must read these values from your router.

---

### Post by lkdhiri on 2005-12-26
Hi,

thanks for your reply. Unfortunately I will not be able to try your suggestion out. After strugling for days making sure the setup was right based on things I know I gave up and Ghosted Windows XP back on the laptop. It's a real pitty since I was hoping to do a total switch to Ubuntu but simply can't spend so much time trying to get the basics right.

--
Update it seems to be a problem when the router is set to shared WEP rather than open. This change seem to have fixed things for me and I am back to using Ubuntu as the only OS on this computer

---

