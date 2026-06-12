---
title: "DSL Speed Issue"
date: 2006-07-10
forum: Desktop Environments
---

### Post by scottieblues on 2006-07-10
Hi all.

I really like Ubuntu.
It has come a long way and is a very nice OS.

However....
After reading through the forums and trying everything that I have seen reccomended, I still can't get my DSL speed to where it should be.

I have a 3Mb feed.
And while using Ubuntu all I get is 1.4 - 1.5.

It runs full steam under Windows.

Does anyone have any other ideas.

I want to keep using Ubuntu.
But not at the price of losing half of my broadband speed.

Thanks in advance.

---

### Post by john_spiral on 2006-07-10
what type of dsl modem do you have, and how are you dialling?

---

### Post by scottieblues on 2006-07-10
> **john_spiral said:**
> what type of dsl modem do you have, and how are you dialling?

I have an Embarq (formerly Sprint) modem and account.

It is running through a Linksys router.

I'm not sure what you mean by how am I dialing?

It's an always on account.

Thanks for replying.

---

### Post by tturrisi on 2006-07-10
OK, the router does the dialing for you.  How are you testing the speed?  Via Firefox?  If so, then try tweaking Firefox:
Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

---

### Post by scottieblues on 2006-07-10
> **tturrisi said:**
> OK, the router does the dialing for you.  How are you testing the speed?  Via Firefox?  If so, then try tweaking Firefox:
Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

I should have told you that I've already done that in Firefox and systemwide.

No matter what Internet app I use to download with, the speeds are about half what they should be.

I've tested it on various sites on the net.

Not sure why it is so slow on Ubuntu, when on Windows everthing is 3Mbs or faster.

---

### Post by john_spiral on 2006-07-10
have you made any changes to the base ubuntu on the networking side?

---

### Post by scottieblues on 2006-07-10
> **john_spiral said:**
> have you made any changes to the base ubuntu on the networking side?

I edited /etc/dhcp3/dhclient.conf

uncommented the "prepend" line and replaced the default with my isps dns addresses.

I did that after reading another post on here saying that might solve the problem.

---

### Post by scottieblues on 2006-07-11
> **scottieblues said:**
> I edited /etc/dhcp3/dhclient.conf

uncommented the "prepend" line and replaced the default with my isps dns addresses.

I did that after reading another post on here saying that might solve the problem.

Fixed it. it was an embarq issue. 
thanks for your help though

---

### Post by marcosr on 2006-07-25
Can you post the text of the entire dhclient.con file after your successfull modification to help me with the same issue ??? Tks

---

