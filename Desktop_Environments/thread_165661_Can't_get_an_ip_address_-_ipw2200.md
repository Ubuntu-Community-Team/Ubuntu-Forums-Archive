---
title: "Can't get an ip address - ipw2200"
date: 2006-04-24
forum: Desktop Environments
---

### Post by scottylans on 2006-04-24
Hi guys,

Since 5.10 is giving me so much problems I did a completely fresh install and  upgraded to dapper using these instructions 
[http://www.ubuntuforums.org/showthread.php?t=137712](http://www.ubuntuforums.org/showthread.php?t=137712)


I've setup wpa supplicant using luca_linux's instructions for 5.10 on setting up wpa supp (included in dapper it seems?)

I edited wpa supp.conf under /etc

I've put in the name of my SSID, the pass, and I've tried 
       scan_ssid=1  (and 2?)

also tried  adding
       pairwise=TKIP	

as suggested.


None the less, I get an ipv6 addres - no ipv4 address.
I've tried manually setting the ip still won't work.
I know the mac security is correct on the a/point because Windows works fine and I know the password is typed correctly.

What could be wrong?

also dmesg | grep ipw seems to come up as if it's working fine?

---

### Post by scottylans on 2006-04-25
[QUOTE=scottylans]Hi guys,

Since 5.10 is giving me so much problems I did a completely fresh install and  upgraded to dapper using these instructions 
[http://www.ubuntuforums.org/showthread.php?t=137712](http://www.ubuntuforums.org/showthread.php?t=137712)


I've setup wpa supplicant using luca_linux's instructions for 5.10 on setting up wpa supp (included in dapper it seems?)

I edited wpa supp.conf under /etc

I've put in the name of my SSID, the pass, and I've tried 
       scan_ssid=1  (and 2?)

also tried  adding
       pairwise=TKIP	

as suggested.


None the less, I get an ipv6 addres - no ipv4 address.
I've tried manually setting the ip still won't work.
I know the mac security is correct on the a/point because Windows works fine and I know the password is typed correctly.

What could be wrong?

also dmesg | grep ipw seems to come up as if it's working fine?[/QUOTE]


I can't ping the laptop from the Desktop either, any idea's?

---

### Post by scottylans on 2006-04-27
Anyone able to help? PLZ

---

### Post by scottylans on 2006-05-01
[QUOTE=scottylans]Anyone able to help? PLZ[/QUOTE]



plz?

---

### Post by scottylans on 2006-05-05
[QUOTE=scottylans]plz?[/QUOTE]

bump

---

### Post by Paloseco on 2006-05-05
If your interface is wlan0 just do "dhclient wlan0" to get an ip from the access point once you´ve found the access point, with kwireless manager for example.

---

