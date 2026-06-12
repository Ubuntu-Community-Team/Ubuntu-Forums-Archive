---
title: "More wlan Broadcom chipset woes"
date: 2006-03-13
forum: Desktop Environments
---

### Post by rogdef on 2006-03-13
Okay, I've finally got my system to recognize that my card is present. But I still can't get it to work. Here is my iwconfig:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:947   Missed beacon:0

Anyone have any ideas on how to get this working? I think I've tried all the tutorials I could find. Thank you!

---

### Post by Ramses de Norre on 2006-03-13
Is it configured under system > administration > networking? Yous essid and accesspoint don't seem right..

If so: what's your /etc/network/interfaces file like?

---

### Post by Mr Squiddy on 2006-03-13
Which Broadcom card do you have and which drivers are you using?  I tried many different drivers until I found the one which worked (I have a Dell but ended up with Acer drivers!)  The iwconfig you posted looked similar to the ones I had when I had the wrong drivers.

Things also improved immeasurably when I enabled SSID broadcasting on my wireless AP.

P.

---

### Post by rogdef on 2006-03-13
Well, I got the wireless card to show up in the network connections list (I configured the static ip, not dynamic), but it still doesn't work. And my eth0 doesn't work when wlan0 is active. 

I have a Broadcom 4306 and am using the bcmwl5 driver. Is there a better one to use? I found some site where someone used lsbcmds and it worked. 

What driver did you use, Squiddy? 

Anyone have any other suggestions? Thank you much!

---

### Post by rogdef on 2006-03-13
Okay, I think I've downloaded the correct driver, because it installed a whole list of stuff it's never done before. Plus it was the driver for my model emachine. So now...

I can select and configure the wlan, but still not get a connection. 

My iwconfig looks like this:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1780   Missed beacon:0

and my interfaces doc has this in it:

iface wlan0 inet static
wireless-essid UNWIRED
address 192.168.1.1
netmask 255.255.255.0

Should I be concerned that the ESSID in iwconfig is not showing the proper ESSID, but it is in the interfaces file?

Please, if anyone can help me, I know I am soooo close to getting this working. Thanks!

---

### Post by rogdef on 2006-03-13
Oh well, I've given up and will probably go out and buy a Netgear Cardbus.

---

