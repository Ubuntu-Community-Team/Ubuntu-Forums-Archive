---
title: "Playing WoW via a proxy server"
date: 2007-08-21
forum: Gaming &amp; Leisure
---

### Post by Yook on 2007-08-21
I've been nearly pulling my hair out at this one. I have a socks 5 proxy which I need to route all WoW traffic through in order to play. All the ports are open on the proxy, so there is no problem on that side.

I've tried tsocks, even with an ssh proxy, but it doesnt seem to help. I've tried the following:

Terminal 1:
ssh -g -D 1080 yook@proxy-box -L 6112:*:6112 -L 3724:*:3724 

Terminal 2:
sudo tsocks wine WoW.exe &

I have tsocks configured to route all traffic via localhost:1080. I can telnet when in tsocks to us.logon.worldofwarcraft.com 3742 no problem, but when using WoW, I get nothing.

Any ideas? I do get 3 'bind: Address already in use' when I ssh into the proxy box. But there definitley nothing running on those ports.

Edit: It seems to work fine with firefox setting proxy to localhost 1080.

---

