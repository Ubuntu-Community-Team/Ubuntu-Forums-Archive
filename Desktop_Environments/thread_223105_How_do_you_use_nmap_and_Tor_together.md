---
title: "How do you use nmap and Tor together?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by reidms on 2006-07-25
Hello.

How do I use nmap and Tor together?

I have checked Tor's man pages and nmaps switches.

---

### Post by reidms on 2006-07-27
Bump

---

### Post by BigCdaAnswer3 on 2006-07-27
> **reidms said:**
> Hello.

How do I use nmap and Tor together?

I have checked Tor's man pages and nmaps switches.


tor is anonymizer software. nmap if for security exploration. i'm not really sure what you are trying to accomplish by putting these guys together?

---

### Post by reidms on 2006-07-27
I know I get that response everywhere.  I am helping my partner in server configuration to better build and configure his server (his first not for him, for a small business) and I am helping him patch  all his holes.  I mean no harm, and if I did, I would not be asking it because I would know.

---

### Post by tturrisi on 2006-07-27
I your friend running a Tor server?
I'm not sure that nmap will even work properly via a tor network.  Tor routes traffic via many tor servers on the www & its intention is to obfuscate tracking and routing info.  Nmap needs to know the routing info in order to work at all.  It doesn't make sense that the 2 would work together.  What did you want to be able to do exactly?

---

### Post by reidms on 2006-07-28
I am running a Tor sever.

We are testing numerous things(we arent the most experienced server guys) such as denying certain IP's and etc.  He is trying to keep people from using Tor(and most other proxy programs)

---

### Post by tturrisi on 2006-07-28
OK, thanks for the info.
But it still does not make sense to run a tor server & prevent others from using it to route traffic through it.  The workability of tor seems to be "the more tor server users, the better the annonimity".  If all you want to be able to do is surf annonimously then use an online proxy server.
```
I want to ban the Tor network from my service.

We're sorry to hear that. There are some situations where it makes sense to block anonymous users for an Internet service. But in many cases, there are easier solutions that can solve your problem while still allowing users to access your website securely.

First, ask yourself if there's a way to do application-level decisions to separate the legitimate users from the jerks. For example, you might have certain areas of the site, or certain privileges like posting, available only to people who are registered. It's easy to build an up-to-date list of Tor IP addresses that allow connections to your service, so you could set up this distinction only for Tor users. This way you can have multi-tiered access and not have to ban every aspect of your service.

For example, the Freenode IRC network had a problem with a coordinated group of abusers joining channels and subtly taking over the conversation; but when they labelled all users coming from Tor nodes as "anonymous users," removing the ability of the abusers to blend in, the abusers moved back to using their open proxies and bot networks.

Second, consider that thousands of people use Tor every day simply for good data hygiene — for example, to protect against data-gathering advertising companies while going about their normal activities. Others use Tor because it's their only way to get past restrictive local firewalls. Some Tor users may be legitimately connecting to your service right now to carry on normal activities. You need to decide whether banning the Tor network is worth losing the contributions of these users, as well as potential future legitimate users.

At this point, you should also ask yourself what you do about other services that aggregate many users behind a few IP addresses. Tor is not so different from AOL in this respect.

Lastly, please remember that Tor servers have individual exit policies. Many Tor servers do not allow exiting connections at all. Many of those that do allow some exit connections might already disallow connections to your service. When you go about banning nodes, you should parse the exit policies and only block the ones that allow these connections; and you should keep in mind that exit policies can change (as well as the overall list of nodes in the network).

If you really want to do this, we provide a Python script to parse the Tor directory.
```

Tor Exit Policies To Restrict Access:
```
ExitPolicy policy,policy,...
    Set an exit policy for this server. Each policy is of the form "accept|reject ADDR[/MASK][:PORT]". If /MASK is omitted then this policy just applies to the host given. Instead of giving a host or network you can also use "*" to denote the universe (0.0.0.0/0). PORT can be a single port number, an interval of ports "FROM_PORT-TO_PORT", or "*". If PORT is omitted, that means "*".

    For example, "reject 127.0.0.1:*,reject 192.168.1.0/24:*,accept *:*" would reject any traffic destined for localhost and any 192.168.1.* address, but accept anything else.

    This directive can be specified multiple times so you don't have to put it all on one line.

    See RFC 3330 for more details about internal and reserved IP address space. Policies are considered first to last, and the first match wins. If you want to _replace_ the default exit policy, end your exit policy with either a reject *:* or an accept *:*. Otherwise, you're _augmenting_ (prepending to) the default exit policy. The default exit policy is:

        reject 0.0.0.0/8
        reject 169.254.0.0/16
        reject 127.0.0.0/8
        reject 192.168.0.0/16
        reject 10.0.0.0/8
        reject 172.16.0.0/12
        reject *:25
        reject *:119
        reject *:135-139
        reject *:445
        reject *:465
        reject *:587
        reject *:1214
        reject *:4661-4666
        reject *:6346-6429
        reject *:6699
        reject *:6881-6999
        accept *:*
```

Here's a good read on nmap & tor.  Nmap is going to find the "true" system anyway if used in SynStealth mode (nmap -v -sS).
[http://talhatariq.wordpress.com/2006/06/05/](http://talhatariq.wordpress.com/2006/06/05/)

---

### Post by reidms on 2006-07-28
No- We are just running the the Tor server while we test the server he made-

Thanks for the information

---

