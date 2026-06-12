---
title: "Do I need to enter DNS"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Howard Blayer on 2006-08-02
I can only access the Internet if I explicitly enter the address of the ISP's DNS server, even though I have DHCP enabled. 

My Windows PC obtains the address of the DNS server automatically from my router via DHCP. Should ubuntu work in a similar way?

Howard

---

### Post by ironfistchamp on 2006-08-02
I had this prob. What I did was go on System > Networking > Eth0 (or whichever interface you use) > DNS and put my default gateway in. Worked from there on.

Hope this helps

Ironfistchamp

---

### Post by Howard Blayer on 2006-08-03
Thanks for that. I just rebooted today and found that my default gateway seems to have been automatically added to the DNS Server list in the Network Settings!

Anyway - it seems to work now so many thanks.

Howard

---

### Post by ironfistchamp on 2006-08-03
Glad its working :)

---

