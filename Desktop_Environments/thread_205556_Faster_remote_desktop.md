---
title: "Faster remote desktop"
date: 2006-06-28
forum: Desktop Environments
---

### Post by ashrack on 2006-06-28
Im migrating my server from W2k3 to UBUNTU DAPPER. In Win I used the RDP protocol which was very fast when connecting from client computers to it. But in DAPPER I find the 'native' remote desktop very slow. Since it uses almost 100% CPU when connecting to it from a client computer with this command:
```
vncviewer server:0
```

Are there any better alternatives??

ps. Ive heard of 'X11VNC' is it good?

SERVERs specs:
Duron 1600+, 512MB RAM, NVIDIA TNT2 PRO using the NV driver.

---

### Post by ashrack on 2006-06-29
anyone

---

### Post by lewmnik on 2006-06-29
Hi 
Not sure if this is what you want:

rdesktop [options] server[:port]

Check man rdesktop if you are a console user or use the gui for easy setup: 

tsclient

---

### Post by ashrack on 2006-06-29
I would need a faster Remote Desktop on my UBUNTU server. So when the client computers on my LAN connect to it it wouldnt be so slow as it is ATM

---

### Post by rmdnet on 2006-08-03
Hi,

Indeed x11vnc is faster than vino, the remote desktop app used on gnome by default. It uses less memory and less bandwith than vino, so I would give it a try.

---

