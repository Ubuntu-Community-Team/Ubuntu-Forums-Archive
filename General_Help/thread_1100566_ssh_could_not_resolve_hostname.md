---
title: "ssh: could not resolve hostname"
date: 2009-03-19
forum: General Help
---

### Post by bebox on 2009-03-19
On my local network i'm using dynamic ip adresses (dhcp)...and i'm using ssh. When i try to connect to a computer on my local network it only works when i type user and ip address (user@ip_address) but not when i type user and hostname (user@hostname). In terminal i get > "ssh: Could not resolve hostname evelin@evelin-laptop: Name or service not known"
Can anybody help me?

And one more thing. On my router I looked on the dhcp server and there are hostnames...

---

### Post by kryptikos on 2009-03-19
There is a difference between DHCP and DNS. If your local network router has a DNS built in you would need to tell ssh to use the DNS. That would be configured in **/etc/ssh/ssh_config**. Something similar to "UseDNS yes". remember you have to recycle the ssh daemon if you modify ssh_config.

If there is not a DNS on your local network then you would have to set up aliases in your **/etc/hosts**file so your client knew about what ip address was assigned to the other computer name.

---

### Post by bebox on 2009-03-19
i'm not using dns...the problem is that everytime the computer restarts it get's a diferent ip addres.so i don't know which computer is which.and when i scan with nmap i only see ip addresses and no hostnames so how should i know on which to connect.

it doesn't detect hostnames.only ip's.

---

### Post by bebox on 2009-03-19
please people...can anyone give me a hint.

---

### Post by Nano_ext3 on 2009-03-19
I always make sure my machine has a reserved or static IP.  Once I do that , port 22 is the default SSH port so do :

```
ssh user@ip_address
```

Doing it via the hostname may work locally, but Ive never had trouble with using the ip address, unless you are typing the hostname improperly

Type "hostname" into the Terminal window to get your full hostname.

Hope this helps,

Cheers!

-Nano

---

### Post by bebox on 2009-03-19
> **Nano_ext3 said:**
> I always make sure my machine has a reserved or static IP.  Once I do that , port 22 is the default SSH port so do :

```
ssh user@ip_address
```

Doing it via the hostname may work locally, but Ive never had trouble with using the ip address, unless you are typing the hostname improperly

Type "hostname" into the Terminal window to get your full hostname.

Hope this helps,

Cheers!

-Nano

Nano thnxs for your reply...i appreciate that.
When i use it with ip's it works but i want to use hostnames because of dhcp ip's change all the time.

My router where dhcp server is setup recognizes host-names...but when i try to connect with shh via hostname to a computer i doesn't work. nmap also doesn't recognize hostnames...

i still didn't figure out what the problem is.

---

### Post by sedawk on 2009-03-19
With DNS names are mapped to IPs and this mapping is more or
less static, so it (nearly) never changes.
So whenever you boot your computers you will not only get a different
IP, but also a different name!

This is a known problem, e.g. connecting to your web server
if your DSL provider changes your IP every x hours.
One solution for this is DynDNS. With DynDNS the static map
of DNS is replaced with a more dynamic map and every machine
sends a message like "I'm machine xyz and my current IP is a.b.c.d".
But you do not really want to run a DynDNS service inside your network !?

The easiest way to fix this issue might be to use static IPs instead
of DHCP.

(I wonder what kind of "names" your router sees, e.g. if he
 maps names to MACs or ...)

---

### Post by issih on 2009-03-19
On a lan there is no host name resolution on ubuntu unless you have a dns server set up, which most home lans do not.

If you are in a heterogeneous network with windows boxes lurking arounf and are expecting those to work you need to look into using either a dns server or enabling netbios resoution.

Alternatively use static ip's and add a the ips to resolv.conf on the appropriate pcs.

One final suggestion is to try using hostname.local. That method should do the hostname resolution via avahi, which seems to work nicely in my setup where I have macs, xp boxes and ubuntu

---

### Post by bebox on 2009-03-19
> **sedawk said:**
> With DNS names are mapped to IPs and this mapping is more or
less static, so it (nearly) never changes.
So whenever you boot your computers you will not only get a different
IP, but also a different name!

This is a known problem, e.g. connecting to your web server
if your DSL provider changes your IP every x hours.
One solution for this is DynDNS. With DynDNS the static map
of DNS is replaced with a more dynamic map and every machine
sends a message like "I'm machine xyz and my current IP is a.b.c.d".
But you do not really want to run a DynDNS service inside your network !?

The easiest way to fix this issue might be to use static IPs instead
of DHCP.

(I wonder what kind of "names" your router sees, e.g. if he
 maps names to MACs or ...)

If DynDNS fixes my problem i want to use it.
My router sees, e.g.:

> Dynamic Addresses:  
        IP Address  	Host Names  	Type
	40.30.5.3 	bebox-laptop 	Dynamic
        40.30.5.5       evelin-laptop   Dynamic

And now when i scan my network i can only see ip addresses and no hostnames. Does DNS service make hostnames visible to the local network? Or do i missunderstand how this works?

---

### Post by fiztlen on 2009-03-19
First of all, I'm assuming this is all internal - laptop A needs to reach desktop B, both using IP's assigned by the router or something else inside the network.  If you're trying to reach in through your router from work etc., you need a DynDNS service and it all gets more complicated.

*** If you're only looking inside, forget DynDNS ***  Dynamic DNS is not your friend either.


Basically, you need something to map from hostname to IP.  This is typically either DNS or /etc/hosts.  Neither is done easily with random IP's (can be done, but probably not worth the effort on a home network).

> My router where dhcp server is setup recognizes host-names...but when i try to connect with shh via hostname to a computer i doesn't work. nmap also doesn't recognize hostnames...

I'm guessing what you mean here is the DHCP server is configured to give a predictable address to particular clients (via MAC address, most likely)?  If so, you're halfway there, but as kryptos said, 
> If there is not a DNS on your local network then you would have to set up aliases in your /etc/hosts file so your client knew about what ip address was assigned to the other computer name. 

So configure a DNS server (on router or otherwise) or add the computers to /etc/hosts:

```

#IP  hostname [[alias1] [...]]
127.0.0.1  localhost
192.168.1.1  machine1.home machine1
```

Obviously you'll need to supply your own hostnames and ips.

Also: resolv.conf points to DNS servers, not any other machine.  Avahi appears to be Apple-specific, so unless you already have it configured for a mac it's probably not going to help a ton.

---

### Post by fiztlen on 2009-03-19
> When i use it with ip's it works but i want to use hostnames because of dhcp ip's change all the time.

Oops, obviously not assigning IP's by MAC address.

Really, switch to static ips and edit /etc/hosts (C:\WINDOWS\system32\drivers\etc\hosts if necessary).  Dynamic DNS is a royal pain, AFAIK DynDNS and competing services are not tooled to provide that (they're designed to find the outside address of your router, and absolutely should NOT be able to see the machines inside).

---

### Post by kryptikos on 2009-03-19
I think we are complicating his issue. If he has a router that he has admin control over he can set up (reserve) static IP addresses in it quickly enough...add the computers' ip addresses that are in his local network in /etc/hosts and then confirm in /etc/nsswitch.conf that it is referencing files first. What type of router do you have...Linksys? Dlink? other?

---

### Post by bebox on 2009-03-19
Ok i understand now...i have dlink. i know how to setup static and all that but i thought there was an easy way to do it dynamic but apparently not. i will probably switch to static.
Guys thank you for your help and that you shared your time.

---

### Post by Cretin_Yes on 2009-04-09
> **bebox said:**
> Ok i understand now...i have dlink. i know how to setup static and all that but i thought there was an easy way to do it dynamic but apparently not. i will probably switch to static.
Guys thank you for your help and that you shared your time.

There is another method you can use to resolve hostnames on ubuntu - and its pretty easy.  Just use hostname.local instead of just hostname.  That is how I access my systems, and I'm pretty new to ubuntu.

---

### Post by adam_kimber on 2009-09-10
> **Cretin_Yes said:**
> There is another method you can use to resolve hostnames on ubuntu - and its pretty easy.  Just use hostname.local instead of just hostname.  That is how I access my systems, and I'm pretty new to ubuntu.

Brilliant. That saved me hours of setting up a DNS server on my network.

---

### Post by bugslayr on 2010-05-30
Hello all,
I had the very same issue.
All your solutions worked but in my case did not handle the problem at its root and did not describe the background. I wanted to see why things happened the way they do ...

For an Ubuntu standard installation (may as well be true for other distributions) the **/etc/nsswitch.conf **suggests the following line for the host name resolution:
**hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4**

What does that mean for the resolver (the lib part which is used by ssh (et.al.) to resolve host names)?
1. If the host name is found in the /etc/ hosts file, things are OK (that's why entering your host name in /etc/hosts does the trick
2. if the host name is found by the **mdns4_minima**l service, OK too.
BUT, if not found the resolver terminates and reports a lookup failure (see nsswitch line).
In this case DNS won't be queried.

So what is the solution?
1. use** /etc/hosts** and skip dns altogether ... I am not sure whether you want to do this
2. place the **dns** service right after the **files** part, or even in front of the **files** part in  [B]/etc/nsswitch.conf
[/B]3.remove the**NOTFOUND **clause in the   **/etc/nsswitch.conf **line; although I don't now whether this may have side effects on other services on the system.

I hope this helps

---

### Post by sodamnmad on 2011-02-13
> **bugslayr said:**
> Hello all,
I had the very same issue.
All your solutions worked but in my case did not handle the problem at its root and did not describe the background. I wanted to see why things happened the way they do ...

For an Ubuntu standard installation (may as well be true for other distributions) the **/etc/nsswitch.conf **suggests the following line for the host name resolution:
**hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4**

What does that mean for the resolver (the lib part which is used by ssh (et.al.) to resolve host names)?
1. If the host name is found in the /etc/ hosts file, things are OK (that's why entering your host name in /etc/hosts does the trick
2. if the host name is found by the **mdns4_minima**l service, OK too.
BUT, if not found the resolver terminates and reports a lookup failure (see nsswitch line).
In this case DNS won't be queried.

So what is the solution?
1. use** /etc/hosts** and skip dns altogether ... I am not sure whether you want to do this
2. place the **dns** service right after the **files** part, or even in front of the **files** part in  [B]/etc/nsswitch.conf
[/B]3.remove the**NOTFOUND **clause in the   **/etc/nsswitch.conf **line; although I don't now whether this may have side effects on other services on the system.

I hope this helps


thank you bugslayr i was getting to the last reply thinking i had gotten nothing but cookie cutter responses about general networking that were pretty useless to my problem.

my setup is a fancy mikrotik that i don't even really understand but _all_ computers in my home network can find each other using ${hostname}.local _except_ the 1 ubuntu box i have. how surprising. anyway, i compared nsswitch.conf on slackware vs ubuntu and i figured i'd share in case anybody else has similar issues:

slackware:
hosts: files dns

ubuntu:
files mdns4_minimal [NOTFOUND=return] dns mdns4

the part that really bugged me is that `dig ${hostname}.local` worked, whereas `ping ${hostname}.local` didn't. ssh didn't either. anyway, hope this helps others.

---

### Post by fslezak on 2011-08-07
Try this:

[email]user@hostname**.local[/email]**

I tried this on SSH, and it worked.

---

### Post by PJSingh5000 on 2011-10-17
ssh://<hostname>.local worked on all of my machines except one...

Sodamnmad, based on your very helpful post, I searched for packages containing nsswitch.conf.

I discovered that this file is provided package libnss-mdns.  On my machine, this package had accidentally been removed.

Reinstalling libnss-mdns solved the problem:
```
sudo apt-get install libnss-mdns
```

For reference, before installing libnss-mdns, /etc/nsswitch.conf contained...
```
hosts:          files dns
```

After installing libnss-mdns, /etc/nsswitch.conf correctly contains...
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

---

