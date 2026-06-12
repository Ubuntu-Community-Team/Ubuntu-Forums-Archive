---
title: "How to VPN to a network using Sonicwall firewall?"
date: 2007-10-02
forum: Desktop Environments
---

### Post by cocotu on 2007-10-02
Just want to know if it is possible to connect to a Sonicwall TZ170.  Normally under windows I use a sonicwall client to VPN to our company LAN.  Would this be possible under Ubuntu? I have seen openssl.org, is this what is needed?  this is one of the last things I need to accomplish in order to move away from Windows.

thanks

---

### Post by ericdegen on 2007-10-05
I'm in the same boat, we use Sonicwall Pros in our organization and need Ubuntu clients to connect to them, I'm kind of lost looking for howtos on the subject please direct me to the right resource - I know I'm not the first person to do this!

---

### Post by cocotu on 2007-10-06
I was lookin into OpenSwan and openSSL, but no solutions yet! let me know if you find somthing concrete! thanks

---

### Post by Baziboune on 2007-10-11
Did you find a way to connect to your workplace's sonicwall VPN?

I am in the same situation than you... no luck yet :-(

---

### Post by cocotu on 2007-10-11
This issue seems like a mistery.  Nobody wants to talk about it!  I search in google and not much information. thanks!

---

### Post by Sgurd on 2007-10-25
> **ericdegen said:**
> I'm in the same boat, we use Sonicwall Pros in our organization and need Ubuntu clients to connect to them, I'm kind of lost looking for howtos on the subject please direct me to the right resource - I know I'm not the first person to do this!

Bump.  Same here.  SonicWALL Pro at work.  I'd like to VPN in from Ubuntu.

Anyone?

---

### Post by cocotu on 2007-10-25
NOBODY wants to talk about this!

---

### Post by ejs7597 on 2007-10-26
Has anyone been able to connect to a Sonicwall TZ170?  I just tried to run the program with wine, but it said it failed to load the IPSec Driver.  Did any of you have any success?

---

### Post by shashipr on 2007-10-28
Have you seen this thread? [http://ubuntuforums.org/showthread.php?t=527423](http://ubuntuforums.org/showthread.php?t=527423).

I am trying it right now.

---

### Post by cocotu on 2007-10-29
is this working for you shashipr?? I feel this issue should be listed at the docs once we know for sure it works!

thanks

---

### Post by shashipr on 2007-11-02
I followed this guide from Sonicwall and it worked just fine.. I was able to establish the connection and ping the machines. I haven't tried anything further. Router is a TZ150.
[http://www.sonicwall.com/downloads/SonicOS_Enhanced_to_Openswan_Using_GroupVPN_with_XAUTH.pdf](http://www.sonicwall.com/downloads/SonicOS_Enhanced_to_Openswan_Using_GroupVPN_with_XAUTH.pdf)
hope this helps.

---

### Post by Cerin on 2008-05-09
I've been researching this as well, but it looks like there are no free or easy ways to do it. Sonicwall 2.5 includes a Linux version of NetExtender (i.e. [http://sonicwall.com/downloads/SSL_VPN_2.5_NetExtender.pdf](http://sonicwall.com/downloads/SSL_VPN_2.5_NetExtender.pdf)). Unfortunately, it can only be downloaded through the "Virtual Office", and I currently only have access to version 2.1. I also noticed that sonicknowitwall.com has videos for configuring the client on Ubuntu, but again, you need to spend $$$ to gain access to the videos, which likely won't help unless you've bought their most recent products.

---

### Post by cocotu on 2008-06-09
so? did anyone solve the mistery? scooby-doo maybe?

---

### Post by HDave on 2008-06-10
I have not gotten this to completely work, but I can share a few nuggets:

1) Lots of good information on the openswan mailing list:

[http://lists.openswan.org/pipermail/users/](http://lists.openswan.org/pipermail/users/)

The main developer there is very active in answering questions.  I have not submitted my question because I am still trying out various things.

2) The pdf referenced in the post above was a big help but I got nowhere until I did a few things (as follows)

3) Disable ICMP redirects via:
```
for f in /proc/sys/net/ipv4/conf/*/accept_redirects; do echo 0 > $f; done
for f in /proc/sys/net/ipv4/conf/*/send_redirects; do echo 0 > $f; done
```

4) Enabling Ip Forwarding
```
	echo 1 > /proc/sys/net/ipv4/ip_forward 
	sysctl -w net.ipv4.ip_forward=1
```

5) the ESP and IKE settings are particular troublesome as you need to crack the code on what DH group means what modp.  Based on my sonicwall settings of crypto-suite and DH group 2 I need:

```
    esp=3des-md5-modp1024		# ????????????? IKE Phase II Settings???? -modp1024 = DH group 2
    ike=3des-md5-modp1024		# ????????????? Sames as ESP???????
```

Note: Diffie-Hellman (DH) Groups
	Group1: 768 bits
	Group2: 1024 bits
	Group5: 1536 bits

6) to find out what the heck is happening when I try to connect i do a:
```
tail -f /var/log/auth.log
```

7) been trying to use wireshark to also examine whats happening, but it is very confusing to me!

8) Openswan has a IRC channel on freenode #openswan

Thats it for now...hope this helps.

---

### Post by Cerin on 2008-06-11
Has anyone tried Sonicwall's new tools? They supposedly fully support a Linux/Ubuntu client now.

---

### Post by HDave on 2008-06-11
> **Cerin said:**
> Has anyone tried Sonicwall's new tools? They supposedly fully support a Linux/Ubuntu client now.

Did some searching and can only find the Windows version.  Can you point the way?

---

### Post by cocotu on 2008-06-11
me too. ONLY windows version. No linux.  Cerin can you provide the link?
thanks

---

### Post by Cerin on 2008-06-11
> **cocotu said:**
> me too. ONLY windows version. No linux.  Cerin can you provide the link?
thanks

Unfortunately, it's only distributed as part of their "Virtual Office" software. You have to find one running at least version 2.5, and click the "Net Extender" link. Then it'll automatically detect what browser/OS you're running and prompt you to download a browser plugin.

---

