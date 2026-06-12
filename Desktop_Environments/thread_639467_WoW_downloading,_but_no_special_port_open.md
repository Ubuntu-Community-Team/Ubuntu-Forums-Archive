---
title: "WoW downloading, but no special port open"
date: 2007-12-13
forum: Desktop Environments
---

### Post by Fixman on 2007-12-13
Im downloading WoW using the Blizzard downloader, but when I run

```
 nmap 127.0.0.1 
```

I get

```

Starting Nmap 4.20 ( http://insecure.org ) at 2007-12-13 11:20 ART
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.131 seconds

```

631 is the printer port, and, theorically, WoW should download from port 3724. Why isn't shown?

---

### Post by dutchman72 on 2007-12-13
For the downloading, Wow uses the torrent ports 6881-6999, generally they aren't shown in scan results. Not really sure why. Port 3724 is only used while playing the game.

I run it on linux as well, and have never seen the ports in a scan listing at any time, the only place I've ever had to deal with it is on my router for the house.

---

