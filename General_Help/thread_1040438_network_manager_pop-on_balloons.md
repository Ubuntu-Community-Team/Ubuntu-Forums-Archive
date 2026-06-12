---
title: "network manager pop-on balloons"
date: 2009-01-15
forum: General Help
---

### Post by nvram867 on 2009-01-15
ubuntu 8.10 comes with real enjoying network manager that pops on balloons on any change,. it does when ubuntu connect to network, it does this when you connect via vino and so on. That is really crappie windows like future that was the very first thing I disabled in windows. I understand that some users may love it, but the distro like ubuntu shouldn’t force others to use it.
I search a net quite a bit and could not find any solution to it. there was a thread on the brainstorm about it but nothing new since november.
anyone has any idea how to hack this ? this is really really annoying.

---

### Post by adult swim on 2009-01-15
try running ```
pkill notification-daemon

sudo chmod -x /usr/lib/notification-daemon/notification-daemon
```
if you want it back ever run ```
sudo chmod +x /usr/lib/notification-daemon/notification-daemon

notification-daemon
```

---

### Post by deadtom on 2009-01-15
You're probably using gnome but knetworkmanager has an option to turn those off. I hate em' too.
Actually I'm not terribly impressed with network manager. It seems to take forever to detect things, doesn't detect wired connections at all and refuses to connect to WPA wireless routers. I'm troubleshooting it but quickly losing hope.

---

### Post by nvram867 on 2009-01-16
thanks, this worked pkill notification-daemon sudo chmod -x /usr/lib/notification-daemon/notification-daemon i am free of the balloons now, it is just sad that you need to kill the daemon to accomplish that. but i rather do that the stair on the hated balloons. one more time, thanks for the tip -:)

---

### Post by PriceChild on 2009-01-16
> **deadtom said:**
> You're probably using gnome but knetworkmanager has an option to turn those off. I hate em' too.
Actually I'm not terribly impressed with network manager. It seems to take forever to detect things, doesn't detect wired connections at all and refuses to connect to WPA wireless routers. I'm troubleshooting it but quickly losing hope.You missed a couple of very important words there... "for me". I find network-manager-gnome works amazingly well for me and couldn't be happier. If you can't connect to WPA then its more likely to be an issue with your wireless cards drivers. Please also file bugs instead of moaning about it in random threads as otherwise it may never get better!

---

### Post by PriceChild on 2009-01-16
Oh you might also want to read about the proposed overhaul of notifications for 9.04 here: [http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

---

### Post by deadtom on 2009-02-17
I installed wicd just a few minutes ago. It took no tweaking, no screwing around and connected to my WPA2/TKIP router with no problems at all whereas Knetworkmanager wouldn't even see it and would puke all over itself every time I tried to manually connect it.

---

