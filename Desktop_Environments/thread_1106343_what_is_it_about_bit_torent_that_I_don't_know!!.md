---
title: "what is it about bit torent that I don't know!!"
date: 2009-03-25
forum: Desktop Environments
---

### Post by bootdoc on 2009-03-25
why is it that every time I try to download a torrent file it never starts.  it just sits there at 0 for freakin' ever.  while we are on the subject of internet transmission,  i can't get any chat client to connect to any server or channel.  I am not behind a firewall.  WTF!

---

### Post by lisati on 2009-03-25
There might not be anyone online seeding the torrents......Frustrating, isn't it?

---

### Post by bootdoc on 2009-03-25
so no one is seeding ubuntu.iso torrents?  whats the point of having them?  why are the torrents on the front download page and one has to search to find the http downloads?  at least those work.

---

### Post by lovinglinux on 2009-03-25
There is always people seeding ubuntu.iso torrents.

Since you also can't connect to irc channels, I'm pretty sure you have some firewall rules that you don't know about.

Do you have moblock or IPBlock installed?

Let's see if you have any firewall rules. Please post the output of:

```
sudo iptables -L
```

After that we will look for other possible torrent issues.

What program you are using for torrent download?

---

