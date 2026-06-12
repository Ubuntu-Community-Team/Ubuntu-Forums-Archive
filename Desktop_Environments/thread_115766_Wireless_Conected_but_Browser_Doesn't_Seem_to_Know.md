---
title: "Wireless Conected but Browser Doesn't Seem to Know it"
date: 2006-01-11
forum: Desktop Environments
---

### Post by gomj0001 on 2006-01-11
Hi:
I get my wireless to connect using the KWifiManager interface. It is conected with signal strenght Excelent and everything. But when i want to browse or ping or chat or anything. The software doesn't seem to realize i am conected. The browse get the poage cannot be displayed and the chat programs just don't conect. ANy help is appreciated.

Thanks :confused:

---

### Post by Dr. Nick on 2006-01-11
you may be "connected" but lack an ip. I havent used kwifimanager, but if you open a konsole type[B]
sudo dhclient wlan0 [/B]to try to obtain an IP. This used to happen to me whereI had a strong signal, but lacked an IP.

 Have you tried to login to the router from your web browser to see if that works?

---

### Post by ssalman on 2006-01-11
I had the same issue when I was setting up my wirless connection with WPA, I don't know if that is what you are trying to do, but if so you need to use WPAsupplicant. good luck :).

---

