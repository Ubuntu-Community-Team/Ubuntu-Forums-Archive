---
title: "Hamachi relayed connection"
date: 2018-03-13
forum: Emulators
---

### Post by meka80 on 2018-03-13
Hello.

I've been trying to play an old video game with an emulator online.  But connecting with Hamachi just won't work, and the reason seems to be a  relayed connection. I haven't been able to turn it into direct like it  should be. All the istructions i've found from the internet are for  windows hamachi and using haguichi as a gui is a bit different. I've  tried to find a way to do that using hamachi through terminal, but it  still remains relayed.


  Help me please and be gentle, i'm just a garbage truck driver :)

---

### Post by jaygambrel on 2018-12-28
I had the same problem.  I edited the override configuration file:

```
sudo nano /var/lib/logmein-hamachi/h2-engine-override.cfg
```

and added the line:

```
Sock.UdpPort         44444
```

This will  limit Hamachi to using this one incoming UDP - 44444 port.  You can choose whichever port you want.  I then opened my firewall  configuration and added in rules to allow IN the following ports:

TCP - 12975
TCP - 32976
UDP - 44444

This allowed me to get a direct connection.

---

