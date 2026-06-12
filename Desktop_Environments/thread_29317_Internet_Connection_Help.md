---
title: "Internet Connection Help"
date: 2005-04-23
forum: Desktop Environments
---

### Post by livelinux on 2005-04-23
I just installed Kubuntu and like it a lot. But there is a major problem that i have had with it. The internet has been going in and out on it. I can sometimes connect to a site using konqueror and sometimes it reports: Host not found.
Also using Kopete I have not been able to get a connection all the time. I am able to download the info but noone else can see that im online and they cannot talk to me.
So i can talk to the internet but the internet cannot talk to me. Any help?
BTW i really like this distro. It would be great to have the internet.

---

### Post by jcdotnet on 2005-04-23
Try ip addess , Ex. 216.239.37.99  

If you can view google , you must to set the DNS

---

### Post by livelinux on 2005-04-24
i got the same error: Could not connect to host

---

### Post by crazybill on 2005-04-24
Always start with ping

Ping to your gateway first.
Then ping to a known site.

For example, if your gateway is 192.168.1.1

ping -c 3 192.168.1.1

ping -c 3 66.17.34.4

See if you get results. That should always be your first step.

BTW fping is a nice little program for UNIX/LINUX/BSD
You can ping to multiple ip addresses to find where a signal stops.

---

