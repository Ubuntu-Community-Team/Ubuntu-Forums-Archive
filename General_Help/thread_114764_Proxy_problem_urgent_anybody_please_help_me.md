---
title: "Proxy problem urgent anybody please help me"
date: 2006-01-09
forum: General Help
---

### Post by raghu on 2006-01-09
I am new to Ubuntu world... even for linux world......

I managed to install the os but, I am not able to set the proxy to my one more system... both are in lan can anybody tell me how to connect the internet to the my..

The following are the settings i did.

1) Both the systems are in lan .... (ssh configured )

2) I configured the proxy in the second machine ( where I want to give the interent connectin ) through system--> proxy settings --> preferences...

3) I have made the settings in the mozilla ( edit --> precerences --> connection settings ) I have given the ip address and the port as 8080 ( i tried with 4480 too ) i could not connect the internet connectin to my second system through my first system...

How can I do that??


Thankyou in advance anybody please help this nascent user to ubuntu.....

Regards,
Raghuveer Reddy

---

### Post by nocturn on 2006-01-09
I believe you can share your connection with FireStarter (you have to install this on your first machine).

After that, it is not the proxy that needs to be set (you can fill in your ISP proxy here), you have to open the network settings on the second machine and enter the IP address of the first as default gateway.

---

### Post by Thirsteh on 2006-01-09
You can indeed share your connection with Firestarter, however personally I recommend reading a guide on Shorewall and sharing with that.

---

