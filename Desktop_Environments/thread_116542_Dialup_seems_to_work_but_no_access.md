---
title: "Dialup seems to work but no access"
date: 2006-01-12
forum: Desktop Environments
---

### Post by mdsmith on 2006-01-12
Hi. This is my first post. I did a search and discovered how to set up the modem and connect to the internet; but, Firefox cannot find any sites. This happened to me with MDK  9.0 and I couldn't find the answer before I moved to a place with no internet. I think the problem then was, the system expected a network because the motherboard has network built in.  By the time I got back on line 9.1 was available and the problem dissapeared.  I have a Motorola external modem and the system did dial and seemed to connect. The network monitor showed the system as active and a few K of transfer. Thanks  Don.

---

### Post by FarEast on 2006-01-13
Hi,

Unfortunately I do not use dial-up connection now.
So I am not sure my suggestion is to the point.  Anyway...

What are you using for ppp connection?

There may be an item which specify the IP address of DNS server.
Have you set it?

regards

---

### Post by Sef on 2006-01-13
Did you check out linmodems?  Link:  [http://linmodems.org/]("http://linmodems.org/")

---

### Post by towsonu2003 on 2006-01-13
check if you can ping 82.211.81.166 and [www.ubuntu.com](www.ubuntu.com)
if the first is ok (which means you are connected to internet) but the second is not, I think there might be a problem with the DNS servers (or your local config of them) of your ISP. not sure though exactly...


PS. 82.211.81.166 is the ip address of [www.ubuntu.com](www.ubuntu.com). your ISP's DNS servers convert [www.ubuntu.com](www.ubuntu.com) to 82.211.81.166 when you type it in firefox...

PS2. Applications>System Tools>Network Tools>Ping (or ping in terminal)

---

### Post by mdsmith on 2006-01-13
Thanks for the replies. I found some things to try in th wiki and I will try the Ping thing. Don

---

### Post by mdsmith on 2006-01-13
Odd, when I booted into Ubuntu the system did the dialup during the boot and it works. I will have to fix the dialup during bootup as I can't tieup the phone that way. I deactivated the connection then reactivated and could no longer access. I am going to try to get KDE installed so I use KPPP which gives me a nice log of the process. Will try again tommorow. Thanks Don

---

### Post by towsonu2003 on 2006-01-14
you could also try wvdial (info inside second link in my signature) to dial out

---

### Post by mdsmith on 2006-01-15
Thanks twosonu2003, I'll try the wvdial. I used that link before but before I could try it the dialup during boot sidetracked me. Don

---

