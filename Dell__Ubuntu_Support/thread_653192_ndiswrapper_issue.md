---
title: "ndiswrapper issue"
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by Rogrogg on 2007-12-29
I've a Dell Inspiron 5100 with a Truemobile 1180 (BCM4303v2) wifi card.

I did some searching and it seems that the bcm43xx doesnt support this particular card, so i went the ndiswrapper route.

I got ndiswrapper installed just fine.  I got the windows .inf and .sys files for the driver and got them installed fine.  

running ndiswrapper -l shows my driver is installed.

I blacklisted bcm43xx, and added ndiswrapper to my /etc/modules

Now here's the issue.  My hardware IS working to some degree because I can see the local wifi networks, but when I connect to my router I get no IP address and no internet signal as a consequence.  I'm thinking that I've overlooked something trivial, but cant seem to put my thumb on it.

if it helps, when i run iwconfig this is the output

eth1      IEEE 802.11b  ESSID:"DangleBerries"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1C:F0:57:59:9B   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and when I run ndiswrapper -l:
bcmwl5 : driver installed
        device (14E4:4301) present (alternate driver: bcm43xx)


Please assist, thanks

Couple more things, when I try to connect it seems like I am but I have no IP (fas as the lappy is concerned), but the routher detects that the wifi is connected and even gives it an IP.  (I've turned off WEP in the meantime, Ill deal with that later)

---

### Post by Rogrogg on 2008-01-02
bump

---

