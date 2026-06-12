---
title: "internet, and a local network issues..."
date: 2006-09-02
forum: Desktop Environments
---

### Post by orlox on 2006-09-02
I've always have trouble when i need to set up a local network, and use a modem connection to internet at the same time. It happens that when i activete the modem (ppp0 interface), the internet connection works perfectly, but if I activate the local network after that (eth0), internet stops working....

Does anyone knoe why???

---

### Post by sdebo on 2006-09-02
I think it is because software you are using (browser) tries to get Internet access through the LAN instead of the modem connection.  You need to sort out network priority.  

Possibly setting DNS and gateway IP addresses in the hosts file could help.  

That is my 2c.  Hope it helps.

---

