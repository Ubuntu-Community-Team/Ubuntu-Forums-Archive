---
title: "Linksys WUSB54G Driver help?"
date: 2008-10-26
forum: Desktop Environments
---

### Post by Pccw9 on 2008-10-26
Hi, I have a Linksys WUSB54G Wireless Adapter that I am trying to get to work with Ubuntu. I have ndiswrapper installed, and got the driver installed properly. When I type "ndiswrapper -l" I get
"wusb54g : driver installed
           device (1915:2234) present (alternate driver: p54usb)"
then, i read that I needed th blacklist the free Linux drivers and the alternate driver p54usb. i did that by adding it to the blacklist and then I rebooted. I then typed in iwconfig. and got 
"wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0"

I then figured it was working and went to the network icon on the panel. and typed in wlan0 and tried to configure it and said error. ? 
Another thing. When i typed in ifconfig, theres another thing like wlan0 there too, would that be a problem?

Regards
Pccw9

---

