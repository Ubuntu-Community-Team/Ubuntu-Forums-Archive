---
title: "Gutsy D630 latitude Intel 3945 wireless"
date: 2008-01-19
forum: Dell  Ubuntu Support
---

### Post by baybe1111 on 2008-01-19
I installed Gutsy from cd onto a Dell D630 latitude which has an Intel 3945 wireless card. (I believe from reading the restricted driver title that the wifi driver was loaded automatically on installation).

I have fixed sound using the 'G' procedure outlined elsewhere on the forums. 

Ethernet networking via cable works fine. WIreless does not. I'm led to believe by the other forums that the 3945 card just works. If so then maybe I'm doing something wrong in the setup. 

Here are the questions.

I've setup using WPA and typed in the key assuming the GUI (System/Administrator/Network/Wireless connection/properties/network password) was asking for an ascii key. Is this correct or should I have used the Hex equivalent of the ascii?

I installed 'WiFi Radar' to see if I could see my network. It says I am connected? Pull up a browser window though and I get nowhere until I reconnect the ethernet cable.

Any Suggestions would be gratefully appreciated?

---

### Post by irish8890 on 2008-01-19
Have you tried turning off the security on your router and tried connecting via wireless?  I have the D630 but with the Dell 1505 Draft 802.11n.  I could not get WPA or WEP to work.  But with wireless security disabled and MAC address filtering set to allow my laptop I can connect.

John

---

### Post by baybe1111 on 2008-01-19
Thanks for your suggestion. I disabled all security/encryption on the router, restarted, but no change. I can still see the connection on wifi radar but cant get any traffic through. 

What else can I try?

---

### Post by ankuryu on 2008-01-22
I would suggest you try the following thread and check it out

[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

  I too had a problem connecting however after   following the instructions given in the thread I could connect to a WIFI WPA2 encrypted network.

   use "wext" for the driver in the wpa_supplicant command.   You may have to load the wpasupplicant if necessary for WPA security.

  check it out

---

