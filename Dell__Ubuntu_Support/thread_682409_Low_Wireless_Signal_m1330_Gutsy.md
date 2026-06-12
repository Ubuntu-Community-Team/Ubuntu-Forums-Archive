---
title: "Low Wireless Signal m1330 Gutsy"
date: 2008-01-30
forum: Dell  Ubuntu Support
---

### Post by ItalianSauce88 on 2008-01-30
Hey Everyone,

Using the Dell Wiki .iso (4.5GB) I completely wiped Vista (and i believe the MediaDirect) partitions and now using Ubuntu Gutsy.

My only issue is that the wireless signal is low than usual. My router is a foot away and signal is 75 - 80%. 

I have tried the bm43 and bcm43xx firmware with the same result. No luck with ndiswrapper either....

I believe Vista had much better signal....

Any ideas????

Thank you

---

### Post by faulkes on 2008-01-30
> **ItalianSauce88 said:**
> Hey Everyone,

My only issue is that the wireless signal is low than usual. My router is a foot away and signal is 75 - 80%. 

I have tried the bm43 and bcm43xx firmware with the same result. No luck with ndiswrapper either....

I believe Vista had much better signal....

Any ideas????

Thank you

When you say no luck with ndiswrapper, do you mean you could not get it to work or that the signal reception was still poor?

Can you provide the output of an "/sbin/iwlist ethX scanning" command?
 - note replace ethX with your interface name (eth0, eth1)

Faulkes

---

### Post by ItalianSauce88 on 2008-01-30
Thanks for the reply....

I could not get ndiswrapper to work aka use my wireless card. The only way I get the blue light to appear and my card to function is with the Restricted Drivers fwcutter firmware either bcm43xx or bm43, Both give me weak signals.

Below is my iwlist output** My network is 'Sauce.' Ubuntu Xwindow says my signal is 73% ~ 81%... looks like iwlist says different?

tim@dell-desktop:~$ /sbin/iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:F6:4F:32
                    ESSID:"Sauce"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-45 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 104ms ago

---

### Post by ItalianSauce88 on 2008-01-30
Ubuntu also says that I'm connected at only 24Mb/s

---

### Post by faulkes on 2008-01-30
> **ItalianSauce88 said:**
> Thanks for the reply....

I could not get ndiswrapper to work aka use my wireless card. The only way I get the blue light to appear and my card to function is with the Restricted Drivers fwcutter firmware either bcm43xx or bm43, Both give me weak signals.



Ok, first thing to know about broadcom/dell wireless with ndiswrapper (and this is my experience) is that it is VERY dependent upon the version of the card and the versions of the driver.  For example, my 600m + wireless will not work with newly downloaded windows drivers under ndiswrapper, however if I roll back to earlier versions (stuff that shipped in C:\DELL) it works just fine.  So that may be an option for you to explore.

> 
Below is my iwlist output** My network is 'Sauce.' Ubuntu Xwindow says my signal is 73% ~ 81%... looks like iwlist says different?


This is not entirely unusual behavior and I wouldn't be overly concerned, there is always a polling delay and iwlist is more direct.

> 
tim@dell-desktop:~$ /sbin/iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:F6:4F:32
                    ESSID:"Sauce"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-45 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 104ms ago

The first thing I see is that your card currently seems to be set to Master mode, which typically means it is acting as a synchronization or an ap itself (see iwconfig man page), I would first try to set via iwconfig the mode to managed to see what changes that makes.

The full output of an "iwconfig ethX" command woud be useful as well.

Faulkes

---

### Post by ItalianSauce88 on 2008-01-30
eth1      IEEE 802.11b/g  ESSID:"Sauce"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:14:6C:F6:4F:32   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=73/100  Signal level=-53 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:528  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by faulkes on 2008-01-30
> **ItalianSauce88 said:**
> eth1      IEEE 802.11b/g  ESSID:"Sauce"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:14:6C:F6:4F:32   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   


That seems a little odd that it's connecting at a 24Mb/s Bit Rate, can you force it up to 54Mb/s using iwconfig

iirc "iwconfig eth1 rate 54M"
 - if it fails to connect to anything, set it back to using auto with "iwconfig eth1 rate auto" or "iwconfig eth1 rate 54M auto"

As a test I would also consider disabling WEP/WPA after doing the above (assuming no changes happen for the better) and then see if anything improves.

Just for my own info, which AP are you using (model/vendor)

Faulkes

---

### Post by ItalianSauce88 on 2008-01-30
OK,

Little progress... I disabled the bcm43xx firmware and configured w/ndiswrapper bcmwl5 and now reach 54Mb/s instead of 24Mb/s, but still weak signal strength. The only other thing i notice is that the GUI and iwconfig now show the same signal strength (before the GUI showed weaker signal than iwconfig)

Still freaked out... thanks for all the help so far.

Using Netgear WGR614 v6 router

---

### Post by faulkes on 2008-01-30
> **ItalianSauce88 said:**
> OK,

Little progress... I disabled the bcm43xx firmware and configured w/ndiswrapper bcmwl5 and now reach 54Mb/s instead of 24Mb/s, but still weak signal strength. The only other thing i notice is that the GUI and iwconfig now show the same signal strength (before the GUI showed weaker signal than iwconfig)

Still freaked out... thanks for all the help so far.

Using Netgear WGR614 v6 router

Alright, well, lets try to move forward a bit here, good to see you're at 54Mb/s
now.

Have you looked at any of the power / antenna options in the router to see if any adjustments can be made?

Is there or are there any other devices near your machine and the router which might be creating RF interference? (note that the iwlist and iwconfig outputs don't show anything but still).

Faulkes

---

### Post by ItalianSauce88 on 2008-01-30
Faulkes, 

With the ndiswrapper, the wireless seems a lot more stable and a bit faster. I topped out at 93% strength with the router 5 ft. away. Still should be 100%, but whatever. And now that I'm getting 54Mb/s, I think i'm going to leave it and call it a mild success. Thanks for the help.

---

### Post by fargle on 2008-02-05
Just to know you're not crazy, mine pretty much completely sucks as well.  Rather than mess with it, I just ordered an IPW3945 card on Ebay for $23 delivered.  I want 802.11a anyway as I also just bought a Cisco AP1230 A-only WAP.

---

### Post by blackest_knight on 2008-04-28
The IWconfig gives it away only 18 dbm transmit power
same as my broadcom chip. its a default mode its proper power is 25 dbm which will make all the difference Ndiswrapper should bring it up however there is a b43 driver which may work better for you (27dbm for my bcm4318 chip). 

you need a better driver either ndiswrapper or b43  hardy can install b43 driver semi automatically there is a hardware driver item under administration you select the driver there and it will download from the internet.

---

