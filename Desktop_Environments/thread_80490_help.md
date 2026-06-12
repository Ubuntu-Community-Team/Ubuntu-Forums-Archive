---
title: "help"
date: 2005-10-22
forum: Desktop Environments
---

### Post by lost1234 on 2005-10-22
I have installed ubuntu only on a pc, it has a dfe-530tx. I can not get an ip address from my isp. ifconfig gives me no ip address but does a mac address.
ifup eth0 does not give me an error message, gives interface already configured.
if i open the dhcp client file, it is empty.
if i go to computer->system config->networking, the etho is listed but disabled.
i can click to enable it but the check leaves when i close it. Also application-> system tols network tools-> devices tab gives me packets sent and recieved and the number increases but when i click on configure to the right , it gives me a log in screen but will not take my root password.

please help me

---

### Post by lost1234 on 2005-10-22
Also sudo dhclient eth0
gives me a no dhcpoffers recieved
no working leases in persistent database - sleeping.


thanks again for any assitance

---

### Post by JamesNorris on 2006-01-02
eth0 might be another network interface (one built onto the mobo?) what chipset is your adapter based on? You might need to install the specific drivers for the modem/net card's chipset. Can't really help more than that..

---

### Post by lnr729 on 2008-01-05
Try putting the 530tx in a different PCI slot.  That made it work for me.  I get the feeling that the IRQ is the problem, in that the drive does not like some IRQs.

---

