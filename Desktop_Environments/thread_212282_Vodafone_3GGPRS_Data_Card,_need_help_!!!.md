---
title: "Vodafone 3G/GPRS Data Card, need help !!!"
date: 2006-07-09
forum: Desktop Environments
---

### Post by niuniek on 2006-07-09
The one I've got is:

Option Model GT 3G Quad, It also has 'QUALCOMM 3G CDMA' written on the back and Serial starts with QL not CL as written in How To's I've read and followed while trying to install it.

I've been trying it on both Ubuntu 6.06 and Kubuntu 6.06, with more success with the latter one, thou I don't quite like the appearance. 
First, I'd like to install it on ubuntu, however I'm a complete newbie to Linux and have no idea how to edit files from the console and could not find such useful thing as Kubuntu has 'Edit as root' therefore I'm not able to edit modules nor any other file that needs to bo edited as root. Read, complete failure at the very begining.

Second, I did install my card on Kubuntu (I was even able to set up a running connection), although there was one 'small' problem, could not surf the net, what I've found out later is that it had some sort of problem with ip address and was using default one starting with 10.xx.xx.xx

I uninstalled Kubuntu, and now have Ubuntu...I'm still not sure if I'll go back to Kubuntu (At least there I've had a connection established)
I've been using How To from this forum as well as the one that's on PHARscape, could anyone tell me if there is any way to install this piece of crap or will I have to uninstall everything and wait for (K)Ubuntu to become more 'windowslike' with it's support for hardware??

---

### Post by niuniek on 2006-07-10
Oki, so I reinstalled Kubuntu and set up connection, thou still not with an outside world ;)
here you've got what was shown on the console:
[SIZE="2"]```

niuniek@niuniek-net:~$ wvdial option internet 3gonly 384k
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+COPS=0,0,"Vodafone UK",2
AT+COPS=0,0,"Vodafone UK",2
OK
--> Sending: AT+CGDCONT=1,"IP","internet";
AT+CGDCONT=1,"IP","internet";
OK
--> Sending: AT+CGEQMIN=1,4,64,384,64,384
AT+CGEQMIN=1,4,64,384,64,384
OK
--> Sending: AT+CGEQREQ=1,4,64,384,64,384
AT+CGEQREQ=1,4,64,384,64,384
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 384000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jul 10 19:48:42 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5425
--> Using interface ppp0
--> local  IP address 10.181.23.212
--> remote IP address 10.64.64.64
--> primary   DNS address 10.11.12.13
--> secondary DNS address 10.11.12.14

```[/SIZE]

I would be very thankful, if anyone can help me with that.
And also, while clicking on KPPP, I get the message that the file /etc/resolv.conf is missing, I've been trying to make one, but the system does not let me do so...???

Thank You in advance,
Michal

---

### Post by Laestrygo on 2006-07-14
Well, to me it seems that you have a connection. Post the result of 'ifconfig' and check if you can ping sth.

---

### Post by pieter_degraeuwe on 2008-03-05
Were you able to solve this ? (and how :-) )

---

