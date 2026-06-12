---
title: "wvdial file for aircel users"
date: 2009-06-23
forum: General Help
---

### Post by dharanitharan on 2009-06-23
Hi friends,
            all are know abt the airtel's gprs scheme has been changed.It suffers our guys who use those facility to access net.Now aircel intro gprs scheme. In order to use this we require [COLOR="Black"]**"wvdial file for aircel"**[/COLOR]... I just try out it n came wit a new file whose content is shown below:

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+CGDCONT=1,"IP","aircelgprs.pr"

Modem Type = USB Modem

Baud = 460800

New PPPD = yes

Modem = /dev/ttyACM0

ISDN = 0

Phone = *99***1#

Password = aircel

Username = Aircel 

Stupid Mode = 1

---

### Post by shumonsaha on 2009-08-28
Hi. I want to use my samsung L 700 phone as a usb modem for internet. I have an aircel connection but the ubuntu wizard doesnt show aircel but shows other service providers. How do I connect 
1. through Usb modem of phone
2. Through bluetooth.

please help

shumon

---

### Post by d_rwin on 2009-08-30
Wvdial is your best option. It is compliant with many ISP.
```
$wvdialconf /etc/wvdial.conf
``` will detect your modem

edit your wvdial.conf password username and Phone details and remove the ';'()semicolon and save
NOTE:: 
dont forget to add 
> stupid mode = 1 at end of wvdial.conf and remove ';'(semicolon)

your wvdial.conf will look like the previous post for aircel users 
then dial in root for first time```
#wvdial&
``` '&' to push it to background job
nest time you can dial as normal user($).
[#wvdial]("http://identi.ca/maji/tag/wvdial") for help

---

### Post by dharanitharan on 2009-08-31
you ve to install a package called wvdial for using these facility

---

### Post by d_rwin on 2009-08-31
yes you need wvdial(linux dialer). ubuntu distributions are shipped with wvdial 1.60(latest). get a package for your distribution from the official page. (small package)

---

### Post by kiran r on 2010-05-04
using aircel gprs on ubuntu 9.10 using blutooth interface without wvdial file....
steps required to follow:

1) setup the connection(from network management i reckon that u know that)

2)fill in apn address which for aircel online is aircelgprs.com or pre  with isp no *99***1#

3)then setup ur homepage on the mobile or just activate gprs symbol(i.e ur gprs connection must be active while connection is to be made)

4)setup the connection--> from connection tab one that with tower symbol choose your device id which follows the pattern "ur device name " followed by device id (like 00:......panu)

5)if ur lucky u will be connected to the net....best of luck...:D

---

