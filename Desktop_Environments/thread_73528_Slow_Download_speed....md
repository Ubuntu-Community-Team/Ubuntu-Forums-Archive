---
title: "Slow Download speed..."
date: 2005-10-09
forum: Desktop Environments
---

### Post by unrealcb on 2005-10-09
I've been the Gnutella furoms and all but there seems to be no solution to my problem...
Its been a week or so since i saw my download speed through Limewire drop to a mere 1kb/sec, i soon found out that Gnome Bit torrent had the same problem, or any other potential p2p program i was advised to try. Normal downloads are at the top speed my connection can offer, i tried many things (proxy, ports change) and things continue to grow strange like this Bitzi web lookup option that appeared in Limewire. Sometimes the searches won't even yield a result and its been a week i'm blocked a 90% of my favorite anime.
I hope to get some help, anyone in this place....

---

### Post by HermanAB on 2005-10-09
Some ISPs throttle P2P traffic.  Trouble is, your ISP won't admit to it over the phone.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by unrealcb on 2005-10-10
Thanks i though about that, but it really felt like i was back to the time i was under windows and eaten by trojan, spyware and adware.... that ain't a possibility right...
Now i'm getting messages about Limewire having connection problems, firewall problems, Limewire in itself was completely restored to default without me interfering.

---

### Post by Hairy_Palms on 2005-10-10
no idea, you sure your isp just isnt haveing bandwidth problems recently?, check their website to see if theyre admitting it

---

### Post by unrealcb on 2005-10-10
Nope ISP website mentionned nothing, most of my friends who still run windows tell me they aren't having any problems...

---

### Post by FLeiXiuS on 2005-10-10
Give it a shot and disable IPv6 if your not using it.  

```

$ sudo gedit /etc/modules

```
Comment out ipv6.
```

..
#ipv6
..

```
Then run, 
```
$ sudo update-modules
```

If this doesn't fix your problems, try going ahead and adding enable port triggering to that port.  If your behind a firewall of anysort.  (routers included).

Hmm other solutions, perhaps your on DSL where your speeds are determined by the distance away from the CO.  As stated above a majority of ISP's are starting to crack down on certain methods of sharing information over the internet.  BitTorrent / Warez being a BIG target.  You could quite possibly be one of those who are stuck inbetween the battle for bandwidth.

---

### Post by unrealcb on 2005-10-11
Thanks for the tip but there is no ipv6 in /etc/modules... 
And for the second part, well i don't really know how to do the "port triggering" stuff...
Thanks again though

---

### Post by FLeiXiuS on 2005-10-11
Do you have a router?  If so, what kind?  If not, do you have a firewall?

---

### Post by unrealcb on 2005-10-12
It seems i don't any of the two. Some minutes ago download speed rose to 4-5 kb/sec when i tried to switch downloads, it dropped down again...

---

