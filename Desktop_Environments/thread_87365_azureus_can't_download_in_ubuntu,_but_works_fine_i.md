---
title: "azureus can't download in ubuntu, but works fine in windows"
date: 2005-11-07
forum: Desktop Environments
---

### Post by michael_salcher on 2005-11-07
I've got a dual boot machine running ubuntu breezy and windows xp. I installed Azureus using Automatix. Azureus starts up and shows a an error message about not being able to load the "update" plugin. But I don't think that matters.
The problem is that Azurues is forever trying to connect to peers, but never actually successfully connects and downloads stuff. When I do the NAT test, I get an "OK". I'm behind a router using DHCP, UPnp is enabled on the router and in Azureus. Azureus works fine on the same computer when using windows.

Could it have something to do with IP forwarding being turned off by default in Ubuntu as mentioned in [another thread]("http://ubuntuforums.org/showthread.php?t=4089")? I don't have a firewall installed.

No other bit torrent clients work in Ubuntu (I tried Gnome Bittorent and BitTornado).

Any ideas?

---

### Post by RAOF on 2005-11-07
What does running
```
java -version
```
at a console say?  If it doesn't say something like
```

java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_04-b05, mixed mode)

```
You need to install java.  Try this [thread]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+1.5+package").

---

### Post by jvictor on 2005-11-07
Did u have port fwding for Azureus setup on the router for windows ? My router needed an IP , so i used static ip rahter than DHCP. If theres jsut one machine jsut use Satc ip .. The ip which u use in windows

---

### Post by eternal on 2005-11-08
[QUOTE=michael_salcher]I've got a dual boot machine running ubuntu breezy and windows xp. I installed Azureus using Automatix. Azureus starts up and shows a an error message about not being able to load the "update" plugin. But I don't think that matters.
The problem is that Azurues is forever trying to connect to peers, but never actually successfully connects and downloads stuff. When I do the NAT test, I get an "OK". I'm behind a router using DHCP, UPnp is enabled on the router and in Azureus. Azureus works fine on the same computer when using windows.

Could it have something to do with IP forwarding being turned off by default in Ubuntu as mentioned in [another thread]("http://ubuntuforums.org/showthread.php?t=4089")? I don't have a firewall installed.

No other bit torrent clients work in Ubuntu (I tried Gnome Bittorent and BitTornado).

Any ideas?[/QUOTE]

no ideas, but i think i may have noticed a similar thing...  i have 1 puter, and i have a HD with ubuntu5.10 and a 2nd HD with winXP and FreeBSD dual-boot.  i physically switch the ide and power cables between them, and all OSes use the same IP and port for azureus.  in XP, azureus gets upto my cable max of around 520Kbps.  i haven't downloaded too many things with azureus on Breezy to be able to tell for sure, but i believe that it is alot slower (maxing at around 120Kbps), and seems to have nat problems, but it is configured exactly the same on both OSes.  xp has a firewall, but breezy doesn't... (and *that* is the topic that i was originally here to look up)

BUT, then i haven't compared them on the same torrent file (different file, different network swarm)...  i just wanted to add a topical comment, maybe there is something here.

i'll update this if i find any more of a trend or otherwise

---

### Post by michael_salcher on 2005-11-08
i've done all the obvious things: i'm using sun's java and enabled UPnP. The problems is that the setup is the same for windows and ubuntu, but it only works in windows

---

### Post by RAOF on 2005-11-08
I suppose it might be IPv6 support?  Maybe you could try option one from [this post]("http://ubuntuforums.org/showpost.php?p=423242&postcount=4")?

---

### Post by michael_salcher on 2005-11-08
i solved the problem and it's actually quite embarassing: i had the proxy turned on in azureus (must have accidentially clicked this option). and i spent hours debugging that problem. ](*,)

---

### Post by mips on 2005-11-08
lol, things like that happens to everybody. You wont make the same mistake again though ;)

---

