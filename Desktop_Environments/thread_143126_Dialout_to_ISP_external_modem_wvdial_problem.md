---
title: "Dialout to ISP external modem wvdial problem"
date: 2006-03-11
forum: Desktop Environments
---

### Post by Jumpy on 2006-03-11
Hi all
I have been trying for about 3 weeks to get my 56K external D-link modem to work with Ubuntu to dial and connect with my ISP. But with out success. 
I have Mepis, Mandrake and Puppy and Windows 98  on the same computer using the same modem and they all work fine, no problems.
However I have read as much as possible and tried a lot but I need help.

Using wvdial I can get to the following stage (almost there)
commands sent as shown by log
ATZ
ok
AT X4 V1 E1 S0=0 &C1 +FCLASS=0
--->modem initialised
--->sending ATDT(isp's phone number)
--->waiting for carrier
ATDT(isp's phone number)
CONNECT  115200
--->carrier detected. waiting for prompt
** Lucent APX Terminal Service **
Login:
Login:
--->looks like a login prompt
--->sending (my login name)
(login name)
PASSWORD
--->looks like a password prompt
--->sending (password)
--->entering ppp session
--->ip address is 218-101-103-79
--->mtu is 1524
--->looks like a welcome message
--->starting pppd at (local date and time)
--->PID of pppd: 13530
--->disconnecting at (local date and time)
--->the pppd daemon died: options error (exit code = 2)

Then it just disconnects from isp.  
The exit code 2 from the man page is: An error was detected in processing the options given, such as two mutually exclusive option being used. 

But which options ???
From my /etc/ppp/options file the following are set
asymcmap 0
noauth
crtscts
lock
hidepassword
noipdefault
passive
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Am I looking in the right places ?? 
Any help would be most appreciated.
If anyone in NZ is using Clear as there ISP and are connecting succesfully I would like to know what settings you are using.
I originally tried to use the Network settings method but with no successs either.
Many thanks in advance
Jumpy

---

### Post by John.Michael.Kane on 2006-03-11
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28up%29%7C%28dial%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28up%29%7C%28dial%29)
[https://wiki.ubuntu.com/UsbAdslModem?highlight=%28modem%29%7C%28usb%29](https://wiki.ubuntu.com/UsbAdslModem?highlight=%28modem%29%7C%28usb%29)

---

### Post by Jumpy on 2006-03-12
Thanks for reply.
I had already downloaded and read the Dialup modem info.
But still cannot solve my problem.
Thanks anyway
Jumpy

---

