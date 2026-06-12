---
title: "can't connect to ntp.ubuntulinux.org"
date: 2005-11-05
forum: Desktop Environments
---

### Post by otware on 2005-11-05
during the long startup procedure, ubuntu is supposed to synchronize its clock with ntp.ubuntulinux.org or something... this always fails on my computer. it doesn't obviously stop me from using the computer, and the time and date settings seem fine (but then again i don't know wot time it's supposed to be most of the time). Im just curious as to whether anyone else has had this problem, if it is at all serious, and what i could do set to the problem right.

---

### Post by dspp on 2005-11-05
[QUOTE=otware]during the long startup procedure, ubuntu is supposed to synchronize its clock with ntp.ubuntulinux.org or something... this always fails on my computer. it doesn't obviously stop me from using the computer, and the time and date settings seem fine (but then again i don't know wot time it's supposed to be most of the time). Im just curious as to whether anyone else has had this problem, if it is at all serious, and what i could do set to the problem right.[/QUOTE]

See if you have ntp support installed. Right-click on the time and then choose adjust date and time. See if periodically synchronize clock with internet servers is checked. If not and you check the box, it will tell you if support is installed or not. Alternatively you can just click the synchronize now button to check your time.

---

### Post by Xian on 2005-11-05
[QUOTE=otware]during the long startup procedure, ubuntu is supposed to synchronize its clock with ntp.ubuntulinux.org or something... this always fails on my computer. it doesn't obviously stop me from using the computer, and the time and date settings seem fine.[/QUOTE]
If this function never works, delays your boot and the clock on your box is correct anyway, then just remove the package which is causing this problem.

```
$ sudo apt-get remove ntpdate
```

---

### Post by otware on 2005-11-05
it doesn't hold up the process for long enough to warrant that really, but it can probably be fixed as dspp says. sadly i don't have access to my ubuntu machine until tomorrow afternoon.

---

### Post by vassie on 2005-11-05
[FONT=Tahoma]I'd say the best way to stop Ubuntu syncing with ntp.ubuntulinux.org would be to remove it from ntpdate

[FONT=Courier New] sudo gedit /etc/default/ntpdate[/FONT]

Comment out[/FONT] [FONT=Courier New]#NTPSERVERS="ntp.ubuntulinux.org"[/FONT]
[FONT=Tahoma]
This way, you don't have to remove any packages

Ben[/FONT]

---

### Post by stevea1210 on 2005-11-05
Is this a symptom to a different problem?  Does your internet connection activate on boot?  It can't sync with the ntp server if it doesn't have connectivity.  The other responses are valid solutions to the symptom, but I am wondering if there is another cause for this.

---

### Post by kvidell on 2005-11-05
I'm having an odd issue relating to NTP...
No matter how many times it downloads and installs NTP, in a row, without removing it... The Time/Date app will _not_ recognize that it's installed...

However if I simply do a "sudo ntpdate time.nist.gov" or whichever time server I feel like using at that given moment, it works just fine... The Time/Date app though...
- Kev

---

### Post by jasongrieves on 2005-11-05
Firewall issue from your ISP perhaps?  That is my problem at work....

---

### Post by rth on 2005-11-05
Could always be that your network connection is not up yet. I know I connect via PPPoE and it seems like ntpdate starts after eth0 but before PPPoE for me. Pain in the arse... But I haven't had time to look into it yet.

---

### Post by Keffin on 2005-11-06
My connection is through a USB modem, which gets initialised during boot but is not ready in time to do the ntp sync on start-up, this seems the most likely reason for the topic creater too. The time never gets wrong enough for me to bother trying to fix it though, I just ignore it :S.

---

### Post by otware on 2005-11-06
i have a wireless network card - so it might not have actually con nected to the network during that period of booting. I know in windows it sometimes takes about 20 seconds after i am logged in to actually con nect to my network.

But could it be another problem? My router is a but funny with Ubuntu - it is fine with xandros and windows though. i had to disable IPv6 in firefox to be able to browse the internet. i think that my router might be slightly incompatible with linux. the router is also an adls modem and a firewall, made by D-Link.

---

