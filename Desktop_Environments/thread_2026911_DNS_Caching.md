---
title: "DNS Caching?"
date: 2012-07-16
forum: Desktop Environments
---

### Post by Acharn on 2012-07-16
My network is not very fast (6Mbps) and is pretty overloaded most of the time. It often takes ten or fifteen minutes to get a particular web page loaded. Not all the time, sometimes things run pretty well and it only takes a minute or two, but trying to connect with my bank in the U.S. in the early afternoon is terribly frustrating, and my comics page often has problems. A big part of the problem is DNS lookup. I hate watching the status bar in Firefox: "looking up gocomics.com" (35 sec) "connecting to gocomics.com" (1sec) "looking up googleads.com" (45 sec) "looking up gocomics.com" (2 min) "connecting to gocomics.com" (5sec) "looking up gocomics.com" (40 sec)...

Back in the 1990s I remember seeing articles about setting up caching nameservers to solve this problem, which was very common then. I want to do that, but I really don't want to set up BIND9. I had some experience with BIND4 or 5, and it wasn't fun. I can do it if I have to, but there should be an easier way.

Up through 11.10, Ubuntu had a program called dnsmasq that could be set up as a nameserver cache. With 12.10, dnsmasq is installed by default along with resolvconf, but the caching has been disabled. There was another program, pdnsd, that is no longer in the repos. Another program, ncsd, seems to be more oriented toward local networking.

Does anybody have any recommendations? I know setting up BIND9 will only take a couple of hours, if that, but it's really hard to force myself to start that project.

---

### Post by papibe on 2012-07-16
Hi Acharn.

This is a  funny coincidence since I just setup bind as caching DNS for my home network :D

I think dnsmasq is your best bet. In 12.04 it is not fully installed, but it's setup as a fixed plugin for Network-Manager (hardcoded for no caching).

These are the steps I would take:
[LIST]
[*]Disable the dnsmasq plugin on Network Manager. Read [here]("http://ubuntuforums.org/showpost.php?p=11923702&postcount=40").
[*]Install dnsmasq and configure it using this [guide]("https://help.ubuntu.com/community/Dnsmasq").
[/LIST]
I hope that helps and let us know how it goes.
Regards

---

### Post by Acharn on 2012-07-16
Wow! Thanks for the help. I was hoping for something like this. I tried just installing dnsmasq before, but didn't know about disabling the plugin. Maybe this will get it.

I certainly would prefer this solution. I gather BIND is easier to work with now than it used to be, and I don't have a network so there would be fewer files to create, but the dnsmasq solution sounds so simple. Will let you know how it goes.

---

### Post by Acharn on 2012-07-16
accidental reposting deleted by poster

---

### Post by Acharn on 2012-07-17
OK, no joy again. Trying to install the dnsmasq package, I get:
```

 * Starting DNS forwarder and DHCP server dnsmasq                               
dnsmasq: failed to create listening socket for port 53: Address already in use

```
This is what I get every time. I think one problem is that the dnsmasq documentation you pointed to is out of date. The developer modified dnsmasq for 12.04, completely disabling dns caching, and the documentation has not been changed to reflect that. I find, way down at the bottom of the page in very small type, "Dnsmasq (last edited 2011-12-15 22:40:34 by astrognome)". So the documentation hasn't been updated to reflect this major change to the software.

Last time I tried this I tracked down this discussion at launchpad: [https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving](https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving). He doesn't mention it on the whiteboard discussion, but I think he hardcoded a block on port 53 into dnsmasq.

I have no idea what "DNS cache poisoning" is, nor the other "security" concerns mentioned. I've seen them referred to, but never explained in a way that allows me to assess my risk. All I know is I have a lot of trouble with DNS lookups on my internet connection. I've always had problems with DNS lookups here in Thailand, probably because the infrastructure has always been overloaded, but it just seems like they are more frequent lately.

Maybe if I remove the whole resolvconf thing?  I don't want to go there.

---

### Post by papibe on 2012-07-17
I wasn't aware of that. My apologies.

This problem won't be fixed any time soon in 12.04, and it has just been fixed in 12.10 Alpha 2 (see [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/959037")).

At this point the only solution I see is to uninstall Network Manager, managing your network using files (/etc/network/interfaces) as if it were a server. That way the regular package dnsmasq won't conflict with NM.

Regards.

---

### Post by Krytarik on 2012-07-17
Why don't you just use faster alternative DNS servers, using the scheme of the very "resolvconf" system you've already mentioned a couple of times, instead of trying to cache the DNS info from your painfully slow default sources?

Popular dedicated and free DNS providers are [Google Public DNS]("https://developers.google.com/speed/public-dns/") and [OpenDNS]("http://www.opendns.com/"), for example, but you can also use any other DNS servers from ISPs open for non-customers you find on the internet.

For instructions on how to set them, overriding the default DNS servers of your ISP, you can see Stéphane Graber's post here:

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Note: Even though the "resolvconf" scheme seems to be used by default for the very first time in Precise 12.04, I had to use it for setting custom DNS servers all the way in Lucid 10.04 already.

Regards.

---

### Post by Acharn on 2012-07-21
> **Krytarik said:**
> Why don't you just use faster alternative DNS servers, using the scheme of the very "resolvconf" system you've already mentioned a couple of times, instead of trying to cache the DNS info from your painfully slow default sources?

Popular dedicated and free DNS providers are [Google Public DNS]("https://developers.google.com/speed/public-dns/") and [OpenDNS]("http://www.opendns.com/"), for example, but you can also use any other DNS servers from ISPs open for non-customers you find on the internet.

For instructions on how to set them, overriding the default DNS servers of your ISP, you can see Stéphane Graber's post here:

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Note: Even though the "resolvconf" scheme seems to be used by default for the very first time in Precise 12.04, I had to use it for setting custom DNS servers all the way in Lucid 10.04 already.

Regards.
 I already use the Google public servers and OpenDns sometimes. Also DNS Advantage. For me they are not fast. They are certainly no better on average than my ISP's servers and sometimes seem worse. I'll chenge them in for a while, and then when resolution becomes intolerably slow, I'll change to some different DNS servers. Thanks for the suggestion, though.

---

### Post by Acharn on 2012-07-21
Well, if it's going to be fixed in 12.10 I might just wait. It'll be out in, what, four months? The more I look at this the more I just want to go take a nap. Back in 1976 this stuff was exciting and fun. Now I'm tired of it and just want it to work. If it doesn't work it takes me working up a lot of energy before I'll go fix it myself, and I'm still reluctant to mess too much with stuff that seems to be an important piece of the system.

---

### Post by jdthood on 2012-12-06
If your nameservers are slow then two good solutions are (1) use other nameservers (e.g., 8.8.8.8 and 8.8.4.4); (2) install a local caching forwarding nameserver.

The dnsmasq process controlled by NetworkManager (call it "nm-dnsmasq") which is enabled by default in Ubuntu Desktop since 12.04 is a fowarding nameserver but not a caching one. Caching is disabled.

In Ubuntu 12.04 you can run standalone dnsmasq instead of nm-dnsmasq. First disable nm-dnsmasq. Edit /etc/NetworkManager/NetworkManager.conf and comment out the line "dns=dnsmasq". Then "sudo restart network-manager". Then install the "dnsmasq" package. You should now see "nameserver 127.0.0.1" in resolv.conf and dnsmasq should be caching DNS queries.

In Ubuntu 12.10 you can run standalone dnsmasq in series with nm-dnsmasq. You don't have to disable nm-dnsmasq; just install standalone dnsmasq and it will forward queries to nm-dnsmasq (which forwards them again upstream) and cache replies.

> ```
dnsmasq: failed to create listening socket for port 53: Address already in use
```

You got this because nm-dnsmasq was still running. You have to disable nm-dnsmasq and "sudo restart network-manager" first.

---

### Post by Acharn on 2012-12-06
Thanks for the attempt to help, but it's just not working. I can't get what you are calling "nm-dnsmasq" disabled. I've been assuming that "commenting out" meant inserting a pound sign in thefirst position on the line, as is true in shell scripts and PERL. Am I wrong?

So after commenting out the line "#dns=dnsmasq" I do:
roger@roger-Aspire-M1610:~$ sudo restart network-manager
network-manager start/running, process 3196

Then I installed dnsmasq using the Software Center.

Then I do:
roger@roger-Aspire-M1610:~$ dnsmasq

dnsmasq: failed to create listening socket for port 53: Permission denied

So apparently nm-dnsmasq is still not disabled. I've also tried restarting the machine, with the same results. According to your post, the problem seems to be that nm-dnsmasq is not being disabled by restarting network-manager.

---

### Post by Acharn on 2012-12-07
OK, I've also tried deleting the "dns=dnsmasq" line from /etc/NetworkManager/NetworkManager.conf and restarting network-manager and rebooting my machine and as before it has no effect. Something is still blocking port 53 and network-manager is still maintaining /etc/resolv.conf /etc/resolv.conf does not show 127.0.0.1. At one point, several months ago it did, but I haven't been able to repeat that.

Incidentally, as I mentioned in an earlier post I already use DNS servers which are supposed to be faster. From time to time as the mood moves me I vary between my ISP's recommended servers and Google's (8.8.8.8, 8.8.4.4) and OpenDNS (207.68.220.220, 207.68.222.222). Sometimes I mix up the order. No difference in performance. At one time I tried another one, called DNSAdvantage, but that didn't have any benefit either so I've forgotten the IP addresses.

---

### Post by jdthood on 2012-12-09
> **Acharn said:**
> Thanks for the attempt to help, but it's just not working. I can't get what you are calling "nm-dnsmasq" disabled. I've been assuming that "commenting out" meant inserting a pound sign in thefirst position on the line, as is true in shell scripts and PERL. Am I wrong?

Inserting a pound sign ('#') at the beginning of the line is the right way to do it.

> So after commenting out the line "#dns=dnsmasq" I do:
roger@roger-Aspire-M1610:~$ sudo restart network-manager
network-manager start/running, process 3196

Then I installed dnsmasq using the Software Center.

Then I do:
roger@roger-Aspire-M1610:~$ dnsmasq

dnsmasq: failed to create listening socket for port 53: Permission denied

So apparently nm-dnsmasq is still not disabled.

The problem here is just that you didn't have root privileges when trying to start the server.  To start the standalone dnsmasq server do

sudo /etc/init.d/dnsmasq start

(although it should have started on package installation).

---

