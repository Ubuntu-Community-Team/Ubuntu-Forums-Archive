---
title: "How do I COMPLETELY disable ipv6?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by bakert on 2006-03-17
I've twiddled Firefox.

(about:config, ipv6 disabled = true)

I've put the appropriate lines in /etc/modprobe.d/aliases

(comment out ipv6 line, or replace with off or add off, or add all three and comment out original line, all with rebooting)

But although Firefox works fine, apt-get does not.  I think because it is trying to use ipv6 (which my router does not support).  All domain name resolution fails and gives the address 1.0.0.0.

How can I truly and utterly obliterate ipv6 from my system?

Thanks,

Tom

---

### Post by ardchoille on 2006-03-17
[QUOTE=bakert]I've twiddled Firefox.

(about:config, ipv6 disabled = true)

I've put the appropriate lines in /etc/modprobe.d/aliases

(comment out ipv6 line, or replace with off or add off, or add all three and comment out original line, all with rebooting)

But although Firefox works fine, apt-get does not.  I think because it is trying to use ipv6 (which my router does not support).  All domain name resolution fails and gives the address 1.0.0.0.

How can I truly and utterly obliterate ipv6 from my system?

Thanks,

Tom[/QUOTE]
I didn't have to mess with /etc/modprobe.d/aliases at all. Here's what I did:

Open Firefox, type about:config into the locatin area, hit enter. in the Filter textbox, type ipv6 and wait for the line to come up. If it is false, double-click it to make it true, then restart Firefox and ipv6 should be disabled.

---

### Post by bjweeks on 2006-03-17
> How can I truly and utterly obliterate ipv6 from my system?

Why? There should be a fix for apt. or get a real router.

---

### Post by ardchoille on 2006-03-17
Sorry about that.. that's what I get for replying before reading the entire post.

---

### Post by mjwood0 on 2006-03-17
> or get a real router.
I'm not really sure how this is helping him...

I would like to say that I too want to disable ALL of ipv6.  I've looked at a lot of different threads on this and I still see it enabled in my list of modules.  It also is using memory and since I have no use for it, I want it gone.

I'll be following this thread closely!

---

### Post by bakert on 2006-03-17
What I REALLY want is for apt to work.  However that can be achieved.

But I thought I'd start with a specific goal because my, "please help me get apt to work" thread got too general and didn't really help!

Also I'm 99% sure I don't use ipv6 for anything and I'm 95% sure that it's the reason that apt can't cope.

Yes, I could get a new router but (a) that costs money and (b) I'd like to be able to fix/understand this in future.

T

---

### Post by dcstar on 2006-03-17
[QUOTE=bakert]What I REALLY want is for apt to work.  However that can be achieved.

But I thought I'd start with a specific goal because my, "please help me get apt to work" thread got too general and didn't really help!

Also I'm 99% sure I don't use ipv6 for anything and I'm 95% sure that it's the reason that apt can't cope.

Yes, I could get a new router but (a) that costs money and (b) I'd like to be able to fix/understand this in future.

T[/QUOTE]
Firstly, if you have correctly removed IPv6 then it applies to all networking from your Ubuntu box, not just Apt.

Secondly, do you have to access the Internet via a Proxy, of so then Apt must be configured to use it.

---

### Post by bakert on 2006-03-18
No proxy.  Set up is Ubuntu->Wireless Router->Wired Router->ISP.

Everything works fine on non-Ubuntu machines on the LAN.  When "Wired Router" supported ipv6 Ubuntu worked fine too.  When I disable ipv6 in Firefox, it works fine.

Hence the desire to completely disable ipv6 (best) or stop apt using it (very close second).

Thanks, Tom

---

### Post by mjwood0 on 2006-03-18
I just ran accross this thread.  I haven't had a chance to try it myself, but is looks promising!

[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

Good luck and let us know how it works!

---

### Post by bakert on 2006-04-02
I think I was mixing up two problems here.  I did have a problem with ipv6 not working with my router.  But the reason apt could not resolve domain names was to do with the nameserver being set by DHCP to be the router's address.

I found a fairly workable answer here (elithrar's post):

[http://ubuntuforums.org/showthread.php?t=141728&page=2](http://ubuntuforums.org/showthread.php?t=141728&page=2)

---

