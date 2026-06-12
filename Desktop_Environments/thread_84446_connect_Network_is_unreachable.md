---
title: "connect: Network is unreachable"
date: 2005-10-31
forum: Desktop Environments
---

### Post by pabc on 2005-10-31
I have a problem. I'm setting up a web server but before it goes live I want to test it.

I've now got apache installed and listening but I cant connect to it with a browser pointing to localhost.

So I try to ping localhost and get the response;

connect: Network is unreachable

I know I've not got a live LAN connection yet but surely I should be able to ping localhost?

Any ideas on where I can start to try and track the problem?

Cheers,

P

---

### Post by suRoot on 2005-10-31
[QUOTE=pabc]I have a problem. I'm setting up a web server but before it goes live I want to test it.

I've now got apache installed and listening but I cant connect to it with a browser pointing to localhost.

So I try to ping localhost and get the response;

connect: Network is unreachable

I know I've not got a live LAN connection yet but surely I should be able to ping localhost?

Any ideas on where I can start to try and track the problem?

Cheers,

P[/QUOTE]


What IP does localhost resolve to when you ping?  It shoud always resolve to 127.0.0.1.

[Jumping on my soapbox]

Sometimes people decide to set the hostname of their machine to 127.0.0.1 with an entry in /etc/hosts similar to:

```
127.0.0.1 localhost.localdomain myhost
```

If you've done this, change it.  If anyone else reading this has done this, change it.  Gnome, and other apps, need to resolve your hostname to work properly.  It's best to configure your DNS properly in the first place, but if you can't (maybe you have a BOFH for a sys admin at work), do something like this in /etc/hosts:


```

127.0.0.1 localhost.localdomain localhost
127.0.0.2 myhost.mydomain myhost

```

[getting off soapbox]

Anyways, what IP does localhost resolve to?

What does 

```
ifconfig lo
```

return?

You should see a line like this:

```
UP LOOPBACK RUNNING  MTU:16436  Metric:1
```

If not, run

```
sudo ifup lo
```

and see if that makes a difference.

---

### Post by pabc on 2005-10-31
Hi,

ifconfig lo returns;

Link encap : Local Loopback
loopback MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisons:0 TXqueue:0
RX bytes:0 (0.0b)
TX bytes:0 (0.0b)

ifup lo returns;
/etc.network/interfaces:2: misplaced option
ifup couldnt read interfaces file /etc/network/interfaces

I'm hopeing that means something to you. But the lack of UP & RUNNING on the loopback doesnt look good. Nor does the fact the ifup returns an error.

Contents of /etc/network/interfaces are;

auto lo
iface lo inet loopback
mapping hotplug
[INDENT]script grep[/INDENT]
[INDENT]map eth0[/INDENT]
iface eth0 net dhcp
[INDENT]network 192.168.0.0[/INDENT]
[INDENT]broadcast 192.168.0.255[/INDENT]
auto eth0


the network and broadcast ips look like the ones i guessed at during ubuntu install but I've since gone into the networking gui and changed the device to dhcp

Does anything stand out as being wrong?

Cheers

P

---

### Post by pabc on 2005-10-31
hmm,

after more reading I started looking at the /etc/network/interface and noticed something strange.

The message 2: misplaced option made my think that there was a problem at line 2 in the interface file. The first line was a comment which spanned 2 lines like it was word wrapped but it wasn't. There was a carrage return meaning ifup was trying to execute what should have been a comment.

I've #'ed it out and rerun ifup eth0.

Now I get DHCP attempting to connect on a few ports, failing (no LAN yet) and sleeping.

The end result is a ping to localhost gets the same message;
connect: Network is unreachable

but at least one error has been removed.

For info, I hadn't been into the interfaces file until I'd seen the 2: misplaced argument error so god know how that get fecked up.

P

---

### Post by pabc on 2005-10-31
apon reboot all worked fine. It was the strange uncommented line stopping ifup working.

P

---

