---
title: "Dansguardian, squid, tinyproxy?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by peizo on 2006-02-11
I know there have been many previous posts on this topic of web content filtering, but I have read them all I'm sure and have been working on this project for far too long.  It's time that I finally get this right.  So here's my setup:

I got an old HP running the latest version of ubuntu with all of the updates.  It has two network cards and I want it to act as a gateway.  I did apt-get to get dhcp3-server, squid, tinyproxy, firestarter, and dansguardian.  The dhcp server and firestarter worked great.  First I just wanted to just be able to have a computer connect through the ubuntu box and to the internet.  I was able to accomplish that through firestarter's connection sharing.  So then it was time to add content filtering so I configured Dansguardian with Squid...all up and running, but no luck.  If I tried to manually configure a browser from another computer to port 8080 to connect to Dansguardian...nothing.  But I could still connect to internet on port 80 like normal...bypassing the proxy, thus the filtering.  So then I read an article on setting up tinyproxy and tried that with Dansguardian.  Same result....

So tonight I do a few tests.  I shut down firestarter and the connection sharing stuff.  Then I manually configure a browser to the proxy on port 8080....and it worked!! Dansguardian was blocking just fine.  So then I try to get email with an external program, and it fails...only connections through port 8080 work....nothing else.  So then I try to share the connection again with firestarter to get everything else working...and it causes Dansguardian to quit. 

I don't understand why I can't get this working.  I just simply want eventually a transparent proxy that redirects all web traffic through Dansguardian, but allows everything other port to bypass the proxy and go straight to the internet.  Is there something I'm doing wrong?

Please, I really need help on this.  Thanks..

Stephen

---

### Post by bb002 on 2006-11-16
well, I haven't moved to using dansguardian with squid yet. But I noticed that firestarter has a short coming when i was setting up just firestarter and squid.

I got everything setup like it was supposed to be but squid was being bypassed. After some more digging I discovered I needed to add a special iptable ```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
```Firestarter wouldn't let me do this. this iptable forces all tcp/ip traffic on eth1 (my lan card) with the destination port of 80 to the default squid port. I previously changed the squid port to 80 but this caused a weird loop with my iptable directive.

I'm going to setup dansguardian soon. Until I do my guess would to change the iptable directive i have above to redirect traffic to the default dansguardian port. Have dansguardian pass "OK" traffic to the squid port, and squid will then fetch the request content from the cache or Internet.

Hope this helps. Once I get everything working I'll start on a howto. Just don't know when I'll have it up because I'm working on this as a side project at work. Depending on how well it works out we might be replacing our current proxy server.

---

### Post by tonhou on 2006-11-16
> I know there have been many previous posts on this topic of web content filtering, but I have read them all I'm sure and have been working on this project for far too long. It's time that I finally get this right.

With respect, can I suggest that you try the howto below, it has been fairly widely used - note it does not use squid! I find it a bit puzzling in your post that you install both tinyproxy AND squid - 2 proxy servers??

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

It may save you a few headaches.

--Tony

---

### Post by bb002 on 2006-11-19
> **tonhou said:**
> With respect, can I suggest that you try the howto below, it has been fairly widely used - note it does not use squid! I find it a bit puzzling in your post that you install both tinyproxy AND squid - 2 proxy servers??

....Nice catch tonhou! Didn't even notice he installed TWO proxy servers. At first I thought you were talking to me until i noticed you weren't peizo. :)

I'll Take a look at that link. Maybe I won't have to make a howto...Finding a good howto on setuping up squid and dansguardian is tough, even disregarding the use of a firewall.

---

