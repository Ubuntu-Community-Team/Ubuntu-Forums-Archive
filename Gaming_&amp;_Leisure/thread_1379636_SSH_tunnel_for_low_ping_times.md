---
title: "SSH tunnel for low ping times"
date: 2010-01-12
forum: Gaming &amp; Leisure
---

### Post by ff8jake on 2010-01-12
Hello everyone,

Currently I am playing Aion (MMO, similar to WoW) and getting pings of around the 400ms range. I also have an Australian friend who plays and was getting pings around 950ms. After doing a bit of reading I discovered lots of people are using SSH tunnels to their Linux VPS servers for game server communication and getting great ping times. I tried this and was pleasantly surprised to see my ping drop to around 190ms and my friend's ping drop to 350ms.

While my ping is fine, I would like to see if I can optimize it any further just out of curiosity and to help my friend get a bit better response. Does anyone know any other settings I can adjust server side (currently my vps is running 9.10 server edition) or in putty to 'optimize' this type of setup? Currently I am using a proxifier and forcing the game's traffic over SSH using SOCKS5 functionality in Putty.

Thanks!

---

### Post by manosx on 2010-01-12
Can you run ssh without encryption? i'm not sure if ssh allows that, but it there any option in putty?
Or what about chosing the cipher with the lowest overhead?

[http://bbs.archlinux.org/viewtopic.php?id=9107](http://bbs.archlinux.org/viewtopic.php?id=9107)
[http://stateless.geek.nz/2004/10/13/scp-performance/](http://stateless.geek.nz/2004/10/13/scp-performance/)
arcfour seems a fast choice

---

