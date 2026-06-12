---
title: "Ubuntu 8.10 MAC Address"
date: 2009-02-17
forum: General Help
---

### Post by Noentry on 2009-02-17
Hi,

I'm trying to change my mac address. I have an atheros chip + madwifi driver. I'm doing these commands:

Firstly I switch to root sudo -s
then 
ifconfig ath0 down
macchanger --mac 00:11:22:33:44:55
ifconfig ath0 up

Everything seems to work, the mac is changed... But I can't connect to any networks. Even to my router. What could be the problem. I tried the hw ether method, same problems. 

Help please :)

---

### Post by Fire_Chief on 2009-02-17
Why exactly are you trying to change your MAC address?

---

### Post by Noentry on 2009-02-17
Education purposes.

---

### Post by sefs on 2009-02-17
Have you tried restarting the network?

```

sudo /etc/init.d/networking restart

```

Happy WEP Cracking :)

---

### Post by Noentry on 2009-02-17
That didn't help. It just tries to connect for about 20 seconds then asks me to enter WPA again...

---

### Post by sefs on 2009-02-17
Sound as if you have mac filtering turned on in your router.  Do you?

---

### Post by Noentry on 2009-02-17
No, I don't.

---

