---
title: "Long Distance VNC/RDP/NX/ETC"
date: 2008-12-29
forum: General Help
---

### Post by fedex1993 on 2008-12-29
So one of my friends live about 3 hours away in austin tx while i live in dallas. Sometimes he needs help with ubuntu sometimes so i want to connect to his desktop to help him walk through. Is there someway that i can get one of these working long distance?

---

### Post by eBoxNet on 2008-12-29
Yes of course you can use any remote access software to control your friends computer.

For vnc your friend need to run the vnc server and you have to run the vnc client, you can start from here : [https://help.ubuntu.com/community/VNC#Accessing%20your%20desktop%20over%20the%20Internet](https://help.ubuntu.com/community/VNC#Accessing%20your%20desktop%20over%20the%20Internet)

an other alternative is to use teamviewer + wine if your friend can't install the server or if you don't have ssh access to your friends computer.

---

### Post by wmoore on 2008-12-29
> **fedex1993 said:**
> So one of my friends live about 3 hours away in austin tx while i live in dallas. Sometimes he needs help with ubuntu sometimes so i want to connect to his desktop to help him walk through. Is there someway that i can get one of these working long distance?Get your friend to go to System --> Preferences --> Remote Desktop and switch on 'allow others to connect to my desktop', making sure to set a strong password. He will also need to configure his router / firewall to forward port 5900 from the internet to his computer. Once done, you can connect to his screen with```
vncviewer <friend's internet Ip Address>:0
```Your friend can get his IP address from [www.whatismyip.com](www.whatismyip.com). For example, if his IP was 123.123.123.123, you would connect by running```
vncviewer 123.123.123.123:0
```

---

### Post by fedex1993 on 2008-12-30
problem is thoe even if it is it seems to lag a heck of alot and not work 100%

---

