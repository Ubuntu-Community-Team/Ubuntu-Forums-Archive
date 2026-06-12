---
title: ":confused: wireless connection error: cannot obtain Ip address"
date: 2009-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vishwasc on 2009-11-14
Hi Guys,
I have recently upgraded my Dell Inspirion 6000 laptop to Ubuntu 9.10 from 9.04 and earlier i was using WICD Network Manager to connect to my Wireless Router as I use the WPA passkey which is not supported by the default network manager.
Since the upgrade my WICD network manager or the default network manager is also not connecting to my wireless router. The authentication is accepted but when it tries to obtain an IP address it fails.

Can someone please help me how can i resolve this error? :confused:

Thank you,
Vish

---

### Post by mr.spaceman on 2009-11-26
I have the same problem, but I can work around it as superuser.

 ```
sudo iwconfig wlan0 essid ESSID
sudo iwconfig wlan0 key KEY
sudo dhclient
```I am still not happy with that solution, but at least it works for me.

---

### Post by vishwasc on 2009-11-26
i am really new to linux so wanted to clarify if you meant that i use the following command in the terminal screen?

vishwas

---

### Post by mr.spaceman on 2009-11-26
Yes, it has to be written in the terminal screen. ESSID is the name of your wireless network, and KEY is the password.

---

### Post by vishwasc on 2009-11-26
Thanks mr.spaceman really appreciate your help!! I will try this out and get back to you either ways if it works or doesn't work, i hate this temp solution, i mean the new version has been launched and no one seems to care about the wireless connectivity and security, why do they release such a unstable version w/o internet connectivity, internet is an essential part of everyone these days and yet its just sidelined and newer versions of Ubuntu was release a month ago. I am highly disappointed with this and I have gone back to Win temporary till this solution is attended and rectified for good.

Thanks,

Vishwas

---

