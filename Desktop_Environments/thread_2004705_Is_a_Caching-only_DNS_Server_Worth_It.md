---
title: "Is a Caching-only DNS Server Worth It?"
date: 2012-06-16
forum: Desktop Environments
---

### Post by Acharn on 2012-06-16
I have a lot of irritation at my World Wide Web connection. Compared with the past, my current ISP is a dream. I'm getting about 6Mbps most of the time, and often web pages open within a few seconds. However I get the Problem Loading Page message way too often, and I've become aware that Firefox is looking up addresses that it just looked up a few seconds ago. The load on the network is very high, here in Thailand, especially on weekends and on weekdays after school lets out and the kids get online.

Back in the early 90's, when I first started using the Internet, I saw articles about setting up a caching DNS server on your local network to help with this problem. Of course, with Web 2.0 it's much worse. I see web pages that are mashups from eight or ten different addresses. The DNS servers are overloaded, and using the open Google servers or OpenDNS doesn't seem to help.

A quick look at how-to's makes it seem like an easy, if tedious, project, so I wanted to ask for opinions. Do many people bother doing this? Does it actually help? I really hate watching the status bar in Firefox, "Looking up slate.com", and then looking up something else, and then "looking up slate. com" again and again and again... Sometimes it takes a minute or longer and then returns the Server Timed Out message.

---

### Post by ratcheer on 2012-06-16
I used to to that when I ran Windows, years ago. I think it was called TreeWalker. Something like that.

Now, I just use OpenDNS. I point my router to OpenDNS and I point all my hosts at the router. OpenDNS also has a lot of optional, additional functionality.

Tim

---

### Post by Acharn on 2012-06-16
Yeah, I had high hopes for that. The added functionality doesn't seem to be something that's useful to me, but I was really hoping for better DNS lookups. Of course my Internet is fairly slow. I have a latency to OpenDNS of between 350 to 700 milliseconds, and according to Internet Traffic Report the Asian region has an average 20% packet drop rate. Anyway, when there are a lot of users on line I get the Page Not Found error about 20% of the time. And I hate seeing the message in the status bar, "Looking up washingtonpost.com" for 30 seconds or a couple of minutes when I just connected to woshingtonpost.com less than a minute ago. Why don't the browsers keep this information in their cache? So what I'm really asking is, would a caching-only name server do that for me? It isn't a lot of work to set up, but it requires some effort. Is it worth it?

---

### Post by sandyd on 2012-06-16
> **Acharn said:**
> Yeah, I had high hopes for that. The added functionality doesn't seem to be something that's useful to me, but I was really hoping for better DNS lookups. Of course my Internet is fairly slow. I have a latency to OpenDNS of between 350 to 700 milliseconds, and according to Internet Traffic Report the Asian region has an average 20% packet drop rate. Anyway, when there are a lot of users on line I get the Page Not Found error about 20% of the time. And I hate seeing the message in the status bar, "Looking up washingtonpost.com" for 30 seconds or a couple of minutes when I just connected to woshingtonpost.com less than a minute ago. Why don't the browsers keep this information in their cache? So what I'm really asking is, would a caching-only name server do that for me? It isn't a lot of work to set up, but it requires some effort. Is it worth it?
You using Ubuntu 12.04?
If you are, you already have a caching dns nameserver called dnsmasq.

Otherwise, check out Namebench -> [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

---

### Post by Acharn on 2012-06-16
> **sandyd said:**
> You using Ubuntu 12.04?
If you are, you already have a caching dns nameserver called dnsmasq.

Otherwise, check out Namebench -> [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Now that you mention it, I see I do have dnsmasq installed and it's running, but what does it do? Well, I'll Google it. And I'll check out Namebench. Thanks for the suggestions. I confess I have qualms about BIND9 because of difficulties my guru had back in 1995 trying to figure out how to set it up, but the current Howto's seem pretty straightforward.

---

### Post by Acharn on 2012-06-17
OK, when I ran "ps ax | grep dnsmasq" there was a process running, but I couldn't configure it until I installed it with apt-get. After that it was ,uch simpler than setting up BIND9. Seems to be working; at least I don't see the "looking up" status as often, just "connecting to." And namebench was very interesting. Took over seven hours to run, but recommended a couple of nameservers that are faster than OpenDNS. I'll see how it works out. I was surprised that the average response time was 1900 milliseconds. I thought it was slower than that. So thank you for your help sandyd..

---

