---
title: "BTGuard (proxy) support in transmission-daemon"
date: 2009-05-05
forum: General Help
---

### Post by gdselzer on 2009-05-05
Is there anyone using transmission-daemon and BTGuard together? I'm having trouble getting it to work. Transmission is working (I'm able to download and upload torrents) however it is not going through BTGuard. I know this because I tried to download the same torrent from a computer on a different network and saw my ip address as the peer (when I should be seeing BTGuard's, right?)

I'm running the Ubuntu package of 1.60b1 on Ubuntu 8.04 server. I tried running transmission-daemon in foreground but did not see any messages related to proxy. Below are the proxy lines from my /etc/transmission/settings.json. Can someone please help me troubleshoot this? What am I missing?

```
"proxy": "canada.btguard.com",
"proxy-auth-enabled": true,
"proxy-auth-password": "mypassword",
"proxy-auth-username": "myusername",
"proxy-enabled": true,
"proxy-port": 80,
"proxy-type": 2,
```

Thanks

---

### Post by papibe on 2010-08-18
I was wondering the same thing. I believe you can do it. Read [here]("http://btguard.com/other.php"). BUT...

For what I understand both transmission clients (gtk and daemon) have the ability to use a proxy just to connect to a tracker. They do NOT use the proxy for peer communications (then leaving a big door open). 

Did you tried it? Any luck?

---

