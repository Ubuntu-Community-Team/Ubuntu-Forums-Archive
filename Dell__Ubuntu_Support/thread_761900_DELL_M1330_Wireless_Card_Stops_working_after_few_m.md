---
title: "DELL M1330 Wireless Card Stops working after few minutes"
date: 2008-04-21
forum: Dell  Ubuntu Support
---

### Post by pipa on 2008-04-21
Hi All,
I have installed Ubuntu gusty on my Dell M1330. Everything works fine but the wireless connection disconnects after few minutes. Then it keep seaching but never reconnects unless I reboot.
My wireless card is Intel® 4965 Wireless-N Mini-card.

Please help.

Thanks!!

---

### Post by pipa on 2008-04-21
Please help. Please dont make me go back to vista.

---

### Post by adw on 2008-04-22
Hi,
do you get any feedback(error messages or the likes)-
whats the signal like?
I can't say i've experienced any problems like that with my m1330, infact the wireless has been solid all the way.

---

### Post by pipa on 2008-04-22
Thanks for ur response.
After few minutes/hours, the wireless disconnects and start searching for network (network is still there with same strength).....and then it rarely connects back. Most of the time, I have to restart to make it work. 
I do not get any signal or error. It just disconnects and keep on searching for ever untill I restart the machine.

Thanks again for ur response!!

---

### Post by pipa on 2008-04-22
Here is the output of iwconfig from the two scenarios:

Connected:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"singh Bros"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:BD:CA:31:3A   
          Bit Rate=11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=85/100  Signal level=-25 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

NOT Connected
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

`Also, my card is wireless N mini card but the output shows IEEE 802.11g. Are these same or is it showing my router?

the wireless works perfectly in windows vista.

---

### Post by adw on 2008-04-22
Hi again, sorry for the late reply.
I had a look at the Dell Ubuntu wiki, and came over this:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

I have not tested it myself, as ive not have the problem you've got- but this is tried and tested by Dell, so im going to trust it.

Apart from that, the Dell ubuntu wiki, [http://linux.dell.com/wiki](http://linux.dell.com/wiki) is a really good resource for m1330 issues, and my only problem with a bad digital mic, was fixed thanks to the wiki :-)

Hope this helps, good luck:-)

---

### Post by pipa on 2008-04-22
THanks a lot!!
I will see if it works for me.

Thanks again.

---

