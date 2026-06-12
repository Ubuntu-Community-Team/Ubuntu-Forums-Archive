---
title: "How do I know whether I am running DNS?"
date: 2009-04-09
forum: General Help
---

### Post by Linuxwho? on 2009-04-09
I need to be sure..  Is it something I check in "sudo-aptitude?"  Is it a file?  I am unsure at this point.  Thanks.

also what is mdns??

---

### Post by paradigm2 on 2009-04-09
> **Linuxwho? said:**
> I need to be sure..  Is it something I check in "sudo-aptitude?"  Is it a file?  I am unsure at this point.  Thanks.

Well if you personally had a DNS Server installed (bind), you'd probably know it.

If you are just using a regular desktop computer changes are your DNS requests are actually answered by your isp.  You probably have your connection set to get that information using DHCP.  Possibly it is ust set to the IP of your router.

To see if you have a nameserver running on your Ubuntu box (I give it 10,000:1 odds) though, just do:

```

ps aux | grep named

```

Does anything show up (besides "grep named" ?)

To see what nameserver (forward) you are using:

From Connection manager:

1. Go to the upper right hand corner of the screen and right click on the icon that looks like two monitors.

2. Select "Connection Information"

3. Find the address listed after "Primary DNS:".  This is your DNS forward.

Sysem wide resolv.conf default name server:

1. Open a terminal window.

2. Type:

```

cat /etc/resolv.conf

```

3. Look for the IP address appearing by "Nameserver"

If you need mor einfo about DNS in general, see:

[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

[http://en.wikipedia.org/wiki/Resolv.conf](http://en.wikipedia.org/wiki/Resolv.conf)

[http://en.wikipedia.org/wiki/BIND](http://en.wikipedia.org/wiki/BIND)

---

### Post by Linuxwho? on 2009-04-09
> **paradigm2 said:**
> Well if you personally had a DNS Server installed (bind), you'd probably know it.

If you are just using a regular desktop computer changes are your DNS requests are actually answered by your isp.  You probably have your connection set to get that information using DHCP.  Possibly it is ust set to the IP of your router.

To see if you have a nameserver running on your Ubuntu box (I give it 10,000:1 odds) though, just do:

```

ps aux | grep named

```

Does anything show up (besides "grep named" ?)

To see what nameserver (forward) you are using:

From Connection manager:

1. Go to the upper right hand corner of the screen and right click on the icon that looks like two monitors.

2. Select "Connection Information"

3. Find the address listed after "Primary DNS:".  This is your DNS forward.

Sysem wide resolv.conf default name server:

1. Open a terminal window.

2. Type:

```

cat /etc/resolv.conf

```

3. Look for the IP address appearing by "Nameserver"

If you need mor einfo about DNS in general, see:

[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

[http://en.wikipedia.org/wiki/Resolv.conf](http://en.wikipedia.org/wiki/Resolv.conf)

[http://en.wikipedia.org/wiki/BIND](http://en.wikipedia.org/wiki/BIND)

Thanks!! ):P Here is my output although at this point I am unsure what it means:

root@ubuntu:/home/owner# cat /etc/resolv.conf
search xxxxxxx.com
nameserver 192.168.1.110
root@ubuntu:/home/owner#


root@ubuntu:/home/owner# ps aux | grep named
bind      4217  0.0  0.9  45644  9896 ?        Ssl  18:11   0:00 /usr/sbin/named -u bind
root      4416  0.0  0.0   3004   756 pts/1    R+   22:12   0:00 grep named
root@ubuntu:/home/owner# 

I am running "server" so I do not have a GUI.  I set my server up with DNS (so I thought but wans/t sure if it was working or even enabled..and SSH per instructions on the Zimbra site a few days ago(I am making an email server cuz I figured it would be a great way to get confused and learn both).   So between doing it a few days ago and figuring out what those intstructions actually did for me, it is a huge learning curve.. ](*,)

This is pretty facinating...I changed my DNS server on my xp box (internal) to the UBUNTU server and it works!!  I guess I did set up DNS.  I will read your links as well.  Thank you.

---

### Post by paradigm2 on 2009-04-09
You DO have DNS running then. :)

This is what the output indicates by the line:

"/usr/sbin/named -u bind" ( I believe the -u bind portion tells named to run as the "bind" user)

But your default resolver uses:

192.168.1.110

in resolv.conf.

Is that the address of this computer, another computer, or a router or such?

edit: to be precise you have what is called a "local DNS server" running.

---

### Post by Linuxwho? on 2009-04-09
> **paradigm2 said:**
> You DO have DNS running then. :)

This is what the output indicates by the line:

"/usr/sbin/named -u bind" ( I believe the -u bind portion tells named to run as the "bind" user)

But your default resolver uses:

192.168.1.110

in resolv.conf.

Is that the address of this computer, another computer, or a router or such?

edit: to be precise you have what is called a "local DNS server" running.

Yes, .110 is my local server itself.  I have been reading a bit already since this post. .. So a "caching" server is probably the best rather than a local one?  or maybe mine is caching?  Because it found google with no trouble and I did not enter that in any config file IIRC.

---

