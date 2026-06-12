---
title: "WPA Supplicant"
date: 2006-10-03
forum: Forum Feedback &amp; Help
---

### Post by ittiam on 2006-10-03
Hi,

I configured my dapper for wifi using ndiswrapper. Daily i work on 2 wireless networks, a secure one and an unsecure one.

I used the wpa_supplicant.conf to start wpa services at start up and it has my secure network entry.

Now if am on the secure wireless network and i want to move to a unsecure network am not able to do so without deleting the wpa_supplicant.conf and restarting the machine. the other way around i had to create the wpa_supplicant.conf and restart. 

What is the way to switch from a secure network to an unsecure network or vice versa without restarting?

---

### Post by wieman01 on 2006-10-04
Best way is to try an applet called NetworkManager which you find in the repositories. I let's you connect to wireless networks "on the fly".

---

