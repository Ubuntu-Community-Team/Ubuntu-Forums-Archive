---
title: "sudo: Unable to resolve host [hostname] - All fixes I've read haven't worked"
date: 2009-03-08
forum: General Help
---

### Post by Googolplex15 on 2009-03-08
**_SOLVED!_**

I'm using the desktop version of Ubuntu 8.04 LTS for a home file server.

Whenever I run sudo in terminal, it says;

```
sudo: unable to reslove host SERVER
```

It still does whatever command I use after sudo, but I can't get this error to go away.

I've tried editing my /etc/hosts, and here is its contents:

```

127.0.0.1 localhost
127.0.1.1 SERVER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Can anybody help?

Thanks in advance :)

---

### Post by taurus on 2009-03-08
What does /etc/hostname say?  Does it just say **SERVER** also?

---

### Post by kerry_s on 2009-03-08
that should be like this:

```
127.0.0.1 localhost SERVER
127.0.1.1 SERVER

```

---

### Post by Googolplex15 on 2009-03-08
Yes, /etc/hostname just reads SERVER

I tried:

```

127.0.0.1 localhost SERVER
127.0.1.1 SERVER

```

but no change.

Do I need to restart?

---

### Post by kpatz on 2009-03-08
Are you using 127.0.1.1 for anything?

Remove the **127.0.1.1 SERVER** line from /etc/hosts and just leave the **127.0.0.1 localhost SERVER** line in and see if that helps.

---

### Post by Googolplex15 on 2009-03-08
Thanks for replying

```
127.0.0.1 localhost SERVER
```

unfortunately did not solve the problem.

Anything else?

---

### Post by kerry_s on 2009-03-08
> **Googolplex15 said:**
> Yes, /etc/hostname just reads SERVER

I tried:

```

127.0.0.1 localhost SERVER
127.0.1.1 SERVER

```

but no change.

Do I need to restart?

yes, try restarting.

---

### Post by Googolplex15 on 2009-03-17
Hey, sorry for delay but the problem's still not fixed.

Any more ideas please?

---

### Post by taurus on 2009-03-17
Post both /etc/hostname & /etc/hosts again.

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by Googolplex15 on 2009-03-17
```
server@SERVER:~$ cat /etc/hostname
SERVER
server@SERVER:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 SERVER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by taurus on 2009-03-17
Probably doesn't matter but try it anyway.  In /etc/hosts, use the tab key instead of just a space key to separate the fields.

```

127.0.0.1       localhost
127.0.1.1       SERVER

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Save it and reboot.

---

### Post by Googolplex15 on 2009-03-17
Thanks for the reply

No change, still getting:

```
sudo: unable to resolve host SERVER
```

The machine is running headless, I am connecting to it via remote desktop, don't think that would make any difference though.

Any more suggestions?

---

### Post by bodhi.zazen on 2009-03-17
Just a guess, but try :

1. changing SERVER to server (lower case). I doubt that will work.

2. in /etc/hosts I think you should try :

```
127.0.0.1 localhost SERVER
127.0.1.1 localhost SERVER
```For some reason Ubuntu now uses 127.0.1.1 , in addition to 127.0.0.1, but I forget why :confused;

---

### Post by Googolplex15 on 2009-03-17
Changing SERVER to server didn't work

Neither did

127.0.0.1 localhost SERVER
127.0.1.1 localhost SERVER


Sigh

Any more suggestions?

---

### Post by bab1 on 2009-03-17
> For some reason Ubuntu now uses 127.0.1.1 , in addition to 127.0.0.1, but I forget why :confused;

@bodhi.zazen,

The reason is explained in section 10.4 of the Debian reference:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns")

---

### Post by bodhi.zazen on 2009-03-17
> **bab1 said:**
> @bodhi.zazen,

The reason is explained in section 10.4 of the Debian reference:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns)

Thanks, I *knew* there was a reason.

---

### Post by Googolplex15 on 2009-03-17
> **bab1 said:**
> @bodhi.zazen,

The reason is explained in section 10.4 of the Debian reference:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns")


"To see whether your system hostname can be resolved to an IP address with a fully qualified domain name, use the hostname --fqdn command."


When I do ```
hostname --fqdn
```

I get:

```
hostname: Unknown host
```

Any more ideas people?

---

### Post by bab1 on 2009-03-17
Which brings us to the OP's situation.  This has been answered before.  See here: [http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

But this does not seem to work for this instance.

I wonder... Has the hostname been changed?  How was it changed?  By Gnome GUI related tools or at the command line? 

See this Google search: [http://www.google.com/search?q=sudo%3A+unable+to+reslove+host&btnG=Go%21]("http://www.google.com/search?q=sudo%3A+unable+to+reslove+host&btnG=Go%21")

---

### Post by bab1 on 2009-03-17
It appears that the problem is in the FQDN lookup.  Do you have a FQDN ie: a suffix such as name.com or name.net ?

---

### Post by Googolplex15 on 2009-03-17
The hostname has been changed numerous times with both the GUI and editing the /etc/hosts file in attempts to fix the problem, however I can't remember editing it before that.

A FQDN suffix such as name.com or name.net?
Erm, I have a website with a .com domain name, if that's what you mean?

I'm 16 by the way and fairly new to Linux and Ubuntu so forgive me if I don't understand some things :)

---

### Post by bab1 on 2009-03-17
Age is not a barrier to using Linux.  :D

Do you have DNS setup on the LAN (local) side?

Does this host have a static IP address?

Is the IP address a valid public address?

---

### Post by Googolplex15 on 2009-03-17
I'm not very clued up when it comes to networking I'm afraid.

Okay here goes:
DNS setup on LAN, I'm guessing no.
If I go onto my router's control panel, on the DNS page, DNS is set to 'Automatic from ISP'

I have not set a static IP address. DHCP?

And I don't know what you mean by a valid public address.

Sorry I can't be of more help there :|

---

### Post by bab1 on 2009-03-17
> **Googolplex15 said:**
> I'm not very clued up when it comes to networking I'm afraid.

Okay here goes:
DNS setup on LAN, I'm guessing no.


So you haven't set up name resolution except with /etc/hosts.
> 
If I go onto my router's control panel, on the DNS page, DNS is set to 'Automatic from ISP'

This would be the WAN side (Public Internet).
> 

I have not set a static IP address. DHCP?

And I don't know what you mean by a valid public address.

How do you have the webserver with the "*a website with a .com domain name...*" setup?> 

Sorry I can't be of more help there :|

If you are using the computer (host) as a webserver and you are usng the FQDN (fully qualified domain name) of server.domain.com, it needs to be resolved to the IP address of the host.  How are you doing that?

---

### Post by Googolplex15 on 2009-03-17
Wow I failed there didn't I... :|


So apparently, no I haven't set up name resolution other than /etc/hosts.


And the website is externally hosted, so completely irrelevant. Sorry about that.

---

### Post by bab1 on 2009-03-17
> **Googolplex15 said:**
> Wow I failed there didn't I... :|


So apparently, no I haven't set up name resolution other than /etc/hosts.


And the website is externally hosted, so completely irrelevant. Sorry about that.

Provide me with the results of this:```
ifconfig -a
```

Edit:  That should be ifconfig not ipconfig.  My bad. :-(

---

### Post by Googolplex15 on 2009-03-17
server@SERVER:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:92:fc:e9:14  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fefc:e914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2996417 errors:0 dropped:2835488960 overruns:0 frame:0
          TX packets:3041339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:230442079 (219.7 MB)  TX bytes:1684881877 (1.5 GB)
          Interrupt:221 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B)

---

### Post by rmeh on 2009-03-17
Hi,
 show me your /etc/nsswitch.conf. Check row where is "host:"

hosts:          files dns

---

### Post by Googolplex15 on 2009-03-17
```
hosts:		mdns dns
networks:       files
```

---

### Post by bab1 on 2009-03-17
How about we do a few more?

First things first.  To send the information in its proper form you can use the icons at the top of the editor.  The button at the bottom that says "Go Advanced" has the more options.  So click on that first.  Now you will see the **#** symbol.  This is to surround your data with [ code ] symbols.  You also can preview your reply before sending it.  Oh yea, it spell-checks too

Now, I need to see the output of:```
cat /etc/network/interfaces
```

And we can do with:```
cat /etc/resolv.conf
```  That is the correct spelling (resolv.conf)

---

### Post by Googolplex15 on 2009-03-17
Yes I have been using the code tags, sorry for not putting that last bit in them, I was distracted by something happening at the time (hence the slow reply) but thanks for reminding me to :)



```
server@SERVER:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet dhcp

```



```
server@SERVER:~$ cat /etc/resolv.conf
search Collingwood
nameserver 192.168.2.1

```

---

### Post by bab1 on 2009-03-17
Looks like you have a few things going on here.  If you have an nsswitch file, you have been playing with winbind.  You need to add the term  "files" (w/o quotes) on the 'hosts:" line.

In addition it appears you have a nameserver at 192.168.2.1 (the router?).    I believe you will find the hostname there.  Also it looks like you are aking to search the domain of Collingwood.  Is SERVER's full name SERVER.Collingwood ?

Edit:  At this point you have a number of little misconfiguration problems to sort out.  Winbind or no.  Collingwood domain or not.  DNS resolution at 192.168.2.1 ?  Static IP or DHCP.  DHCP makes it hard to use host files.

---

### Post by Googolplex15 on 2009-03-17
Right we're getting somewhere.

I have changed /etc/nsswitch.conf to read:

```

hosts:		mdns dns **files**
networks:       files

```


Collingwood is the SSID of the router.

SERVER's full name is not 'SERVER.Collingwood', I'm fairly sure it's just 'SERVER'

---

### Post by bab1 on 2009-03-17
Put files first. Comment out the reference to Collingwood, like so:```
# search Collingwood
``` and Bob's your uncle!

---

### Post by Googolplex15 on 2009-03-17
Thank you so much! :D

I thought for a moment there I'd totally buggered it up, I restarted after I added 'files' to the END of the line, and I couldn't connect to the machine with remote desktop using VNC Viewer. Previously I was using the server name 'SERVER', which didn't work when I just tried it. 'server' (in lower case), however, worked, so all is fine :)

I have just made the changes you mentioned, and all is working, back with the capitals 'SERVER'.

Thank you very much bab1 :D

---

### Post by bab1 on 2009-03-17
And you have tried **sudo**?

---

### Post by Googolplex15 on 2009-03-17
Yep, and it's working without the error :)

Thank you for your time and effort :D

---

### Post by bab1 on 2009-03-17
Great!

---

