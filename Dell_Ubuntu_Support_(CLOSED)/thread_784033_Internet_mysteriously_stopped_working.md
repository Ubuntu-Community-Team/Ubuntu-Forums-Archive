---
title: "Internet mysteriously stopped working"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HanZo on 2008-05-06
I have a Dell XPS 1330, one of those that come with ubuntu, just that I installed it myself (hardy).
I started with one of the betas and then upgraded every time there was something to upgrade.

Everything went fine until today, when I tried to wake the laptop from suspend, and as so often, it did not come back. I restarted X (CTRL+ALT+BSPC) just to find the internet not working anymore.
Rebootet the whole thing, but still... no internet.

Funny thing is, the wireless card works, I can access network shares, firefox even shows it connects to the specified domain, but then it won't open the page (nor download mail, nor download packages through apt... nor do anything that needs stuff to be sent over the internet.

Internet works with vista on the same machine (so it's not the router or anything hardware related)

My suspicion is that it has something to do with ports blocked by who knows what (not ufw, 'cos I checked, it's disabled)

So... what can I try? What can I do... other than reinstalling hardy from scratch...

---

### Post by HanZo on 2008-05-06
hmm... after some more testing it seems the computer just doesn't want to get the DNS. Somewhere there's something that needs to be adjusted, I just can't figure out what it is...

---

### Post by emerbomb on 2008-05-06
Try a different internet cord i had the same problem

---

### Post by HanZo on 2008-05-06
I tried almost everything now... but I just can't nail down the problem.

At home, where I connect directly to the router with eth connection is fine.
Here at work the connection scheme is bit more complex... I am connected to a basestation (Apple airport) which connects to the main router.
I tried to connect to the main router directly with eth, tried to use a bridged connection through my mac pro, tried to set the DNS addresses by hand, tried to use DHCP instead of roaming... everything...
No matter what I do I always get the same problem. It seems to be the router anyway.

---

### Post by HanZo on 2008-05-06
well, it seems like ubuntu was not the problem after all, but the lousy router the internet provider gave us for free. It does have a problem with ecn turned on for ipv4 and with window scaling. turning everything off solved the problem.

basically here is what I did (after hitting "sudo su")
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
echo 0 > /proc/sys/net/ipv4/tcp_ecn

or just put this in /etc/sysctl.conf and reboot:
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_ecn= 0

it might not be useful for the many of you who stumble upon connection problems (like pages only half loading)... but who knows... it helped me :)

---

