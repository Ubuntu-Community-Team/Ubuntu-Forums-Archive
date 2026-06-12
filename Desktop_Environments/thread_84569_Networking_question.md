---
title: "Networking question"
date: 2005-10-31
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-31
I am on the road for the next three weeks.  I am trying to connect to the internet using the hotel's high speed (ethernet, not wireless) connection.

Under windows, I have to turn off my firewall before I can connect.  I have firestarter running under Ubuntu.  I am not able to connect with Ubuntu even if I stop firestarter using the "Stop Firewall" option.  

On both windows and Ubuntu, when I open firefox, the status bar says "looking for 'domain name'.com.  As soon as I turn off the firewall in windows firefox will connect.  I would like to be able to do the same under Ubuntu.  I have not done any special connection settings for my Ubuntu eth0 connection.

Has anyone seen this who may have an answer for this problem?

---

### Post by mgor on 2005-10-31
i haven't used firestarter myself, but does 'Stop firewall' really remove all the rules?

check with
```
sudo iptables -L
```

if it dosen't look like this
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

then flush all the rules
```
sudo iptables -F
```

and try again.

---

### Post by mrmcctt on 2005-10-31
Thanks for the quick reply.  Unfortunately this did not work.  When I ran the ```
sudo iptables -L
```

Everything showed 'DROP' instead of showing 'ACCEPT'.  I am having a hard time with copy and paste outputs to show you because I have to jump between windows and Ubuntu.

When I tried ```
sudo iptables -F
``` I was unable to open firestarter or network-admin to try to configure the connection.

Still no luck with connecting to the internet.  I did get into firestarter and try to, basically, allow everything and it still didn't work.

Any other suggestions?

---

### Post by mgor on 2005-10-31
ah, stop firewall in firestarter probably then drop's _everything_. after you've flushed the rules, list the rules again to check if says accept instead of drop.

how do you get your IP adress? static or dynamic?

check with ifconfig if you've got a IP adress.
if you've got one, try to ping the default gateway.
```
route | grep default | awk '{ print $2 }'
```

---

### Post by mrmcctt on 2005-10-31
I know I'm getting an ip.  It's DHCP and is 10.59.241.xxx.  The default gateway is 10.59.241.xxx.

This is acting like it's blocking any type of DNS.  I get to the gateway, get an IP from their DHCP server (router?) but cannot resolve any internet addresses.  If that makes sense and I am far from a guru on this.

I'll try to run the ```
sudo iptables -L
``` after everything else but basically I have to reboot to do anything with th system after doing the ```
sudo iptables -F
```.

I even have to do a ctl>alt>bksp just to get to a point where I can reboot the system after running this.

---

### Post by mgor on 2005-10-31
ah, i forgot a step.
check /etc/resolv.conf, it contains the nameservers (dns).
try to ping the ones that are listed there. 
se if you have any /etc/dhclient-*-hooks, it's script that allows you to control how dhclient behave.

i know a friend of mine had a problem running iptables -F with firestarter in fedora. try flushing the rules without first stopping firestarter. you wrote in an earlier post that you had tried allowing anything and it still didn't work? do that again (don't flush the rules) and then list the rules to se if it's accepting instead of dropping?

anyway, it might be a dns server problem. check what you get in windows (ipconfig /all) and manually add them to /etc/resolv.conf if the above dosen't work.

---

### Post by dbott67 on 2005-10-31
I was going to suggest checking the /etc/resolv.conf also.

You may also want to run a traceroute to a known IP address (google=72.14.207.99)
```
dbott@breezy:~$ traceroute 72.14.207.99
traceroute to 72.14.207.99 (72.14.207.99), 30 hops max, 38 byte packets
 1  192.168.1.1 (192.168.1.1)  5.360 ms *  3.588 ms
 2  123.wxyz.net (123.123.123.123)  17.789 ms  14.432 ms  13.678 ms
 .
 .
 .
16  72.14.236.130 (72.14.236.130)  53.647 ms  56.348 ms  54.306 ms
17  72.14.207.99 (72.14.207.99)  43.263 ms  44.120 ms  45.460 ms
```

BTW, traceroute may need to be installed via synaptic; you can also try APPLICATIONS --> SYSTEM TOOLS --> NETWORK TOOLS to run a trace.

If you can run a successful trace to a known working IP, then it may be a DNS issue.  If you cannot make it past the gateway IP, then it may be something else.

Can you print the output of the following commands:
[LIST=1]
[*]ifconfig
[*]cat /etc/resolv.conf
[*]route
[/LIST]

Thanks,
Dave

---

### Post by mrmcctt on 2005-10-31
> check /etc/resolv.conf, it contains the nameservers (dns).
try to ping the ones that are listed there. 

There is an address (domain name) to my home ISP (domain.name.com) and to another dns server I found on google (secondary.org).  There was also an ip address to the dns server here. 168.95.1.1 .  I pinged this ip and everything was fine.  No lost packets.

> You may also want to run a traceroute to a known IP address (google=72.14.207.99)

I will try this also.  On a side note, I have tried to ping 'www.google.com' (not the ip but the url) and got no reply.

Network-admin has a traceroute that I think will work.

Thank you both for your time and I'll let you know what happens.  I'm just confused because I've never had what amounts to a 'default' setup for networking not work.

---

### Post by mrmcctt on 2005-10-31
I tried to run a traceroute to the ip address that you gave me for Google.  Hop one was to the ip address given to my machine and then I got a no route message.

I'm looking to see if I packed my thumbdrive so I can tranfer the results of the three commands you asked about.  Like I said earlier, I'm jumping to windows to post this and Ubuntu to check things out.

---

### Post by mrmcctt on 2005-10-31
dbott67

Here's the ifconfig:

```
rlodge@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:D5:77:9C
          inet addr:10.59.241.42  Bcast:10.59.241.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fed5:779c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9676 (9.4 KiB)  TX bytes:15378 (15.0 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:189479 (185.0 KiB)  TX bytes:189479 (185.0 KiB)

rlodge@ubuntu:~$
```

Here's the cat /etc/resolv.conf

```
rlodge@ubuntu:~$ cat /etc/resolv.conf
search hot.rr.com secondary.org
nameserver 168.95.1.1
rlodge@ubuntu:~$
```

And finally, here's the route.

```
rlodge@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.59.241.0     *               255.255.255.0   U     0      0        0 eth0
default         10.59.241.99    0.0.0.0         UG    0      0        0 eth0
rlodge@ubuntu:~$
```

Again, thanks for your help.  I hope you can see something in this that I don't.  Like I stated earlier, under windows the only way I can connect is to first shut down my firewall (zone alarm).  Under Ubuntu I run Firestarter as the frontend for the iptables (if that's the correct way to put it).

---

### Post by dbott67 on 2005-10-31
It appears as though the nameserver settings in **/etc/resolv.conf** are still stuck on your home ISP.

Can you print out your IP settings from Windows and post them here?
```
ipconfig /all
```
Type the above command from the command line (for Windows XP) or '**winipcfg**' for Win9x.

Basically, what I'm looking for is the DNS server that Windows is using.  For example, if Windows reports that the DNS server is 10.59.241.1, you need to change your **/etc/resolv.conf** to the following:
```
# search hot.rr.com secondary.org
# nameserver 168.95.1.1
nameserver 10.59.241.1
```
You can see that I just commented out your first 2 lines and then added a new nameserver line with the DNS server reported by Windows.  Just be sure to use the one Windows provides, and not the one from my example! :) (well, unless I happened to guess the actual DNS server ;) )

-Dave

---

### Post by ratsalad on 2005-10-31
If the problem is indeed DNS, why not consider just setting up BIND? If I remember right, you would just add 127.0.0.1 as your nameserver in resolv.conf. No ports to open, etc. it should just work :)

---

### Post by mrmcctt on 2005-10-31
Here's the ipconfig /all ```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Jon>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : HOME4
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-02-3F-D5-77-9C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.59.241.42
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.59.241.99
        DHCP Server . . . . . . . . . . . : 10.59.241.99
        DNS Servers . . . . . . . . . . . : 168.95.1.1
        Lease Obtained. . . . . . . . . . : Monday, October 31, 2005 9:01:30 PM
        Lease Expires . . . . . . . . . . : Tuesday, November 01, 2005 2:01:30 A
M

Ethernet adapter Wireless Network Connection 3:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Atheros AR5004G Wireless Network Ada
pter #2
        Physical Address. . . . . . . . . : 00-90-96-C1-A5-59

C:\Documents and Settings\Jon>
```

Looks like the same DNS server data.  I did comment out the others (hot.rr.com etc.) Still no luck.

> If the problem is indeed DNS, why not consider just setting up BIND? If I remember right, you would just add 127.0.0.1 as your nameserver in resolv.conf. No ports to open, etc. it should just work 

ratsalad, I'll try that.  Are there any downsides to this like gaping security breaches?

---

### Post by ratsalad on 2005-10-31
[QUOTE=mrmcctt]ratsalad, I'll try that.  Are there any downsides to this like gaping security breaches?[/QUOTE]

BIND does have a history of security holes. But with anything like this, you must take precautions. Keeping it up to date (sure.. with Ubuntu, that's not a problem). I don't know about on Ubuntu, but on a lot of distributions daemons like named are set up to run in a chroot jail.

Though, now seeing that 168.95.1.1 was correct in your resolv.conf, I seriously doubt DNS is the problem.

---

### Post by mrmcctt on 2005-10-31
Nope...still no connection.  Firefox keeps looking for google.com but never connects. I have tried other wb addresses and even the ip address to google and no luck.

I'm still inclined to believe that it's a problem due to the firewall.  This is a hotel network.  In my travels I have seen hotel networks that 'required' you to log in with IE before they would let you connect. After your initial log in you could use pretty much any browser.

In this hotel, under windows, I have to disable my firewall to connect.  I'm not 100% sure that the firewall in Ubuntu is actually disabling.  I click (in firestarter) to stop the firewall and then close firestarter.  When I open firestarter again, it's active.  I'm not sure how to completely shut it down.

I did try adding 127.0.0.1 to the resolv.conf and that sisn't change anything.

Thanks though for the advice.

---

### Post by ratsalad on 2005-10-31
[QUOTE=mrmcctt]Nope...still no connection.  Firefox keeps looking for google.com but never connects. I have tried other wb addresses and even the ip address to google and no luck.

I'm still inclined to believe that it's a problem due to the firewall.  This is a hotel network.  In my travels I have seen hotel networks that 'required' you to log in with IE before they would let you connect. After your initial log in you could use pretty much any browser.

In this hotel, under windows, I have to disable my firewall to connect.  I'm not 100% sure that the firewall in Ubuntu is actually disabling.  I click (in firestarter) to stop the firewall and then close firestarter.  When I open firestarter again, it's active.  I'm not sure how to completely shut it down.

I did try adding 127.0.0.1 to the resolv.conf and that sisn't change anything.

Thanks though for the advice.[/QUOTE]


One more idea for you then. Try taking down iptables via the init script.

sudo /etc/init.d/iptables stop

---

### Post by mrmcctt on 2005-11-01
> One more idea for you then. Try taking down iptables via the init script.

sudo /etc/init.d/iptables stop
  	
Reply With Quote

That command gives me an error.  After checking /etc/init.d there is no iptables program to stop.  It doesn't exist.

---

### Post by mrmcctt on 2005-11-01
I have noticed that when I try to ping anything past the gateway I am sending packets like crazy but nothing is getting back to my system.  100% lost packets.  They're getting sent but nothing is coming back in.  This is with Firestarter started or stopped and when Firestarter is running, have tried to allow everything and still I can't receive anything.

---

### Post by mrmcctt on 2005-11-01
Well, I finally got online with Ubuntu.  I finally just got fed up (not with you guys but that I couldn't connect) and removed Firestarter.

I then rebooted the system and "Poof" I'm online.

Thank you everyone for your help and rest assured that I will be looking for advice on a better firewall than what I just removed.  I know that Firestarter is just a frontend for the iptables (or so I was led to believe on this forum) but if it keeps me from getting my work done, it ain't for me.

The problems I have had here remind me of when I worked for a cable company setting up internet access for customers.  I dreaded seeing a computer with McAfee on it.  McAfee firewall had a habit of not disabling when disabled but rather completely blocking network connections.

---

### Post by dbott67 on 2005-11-01
Glad to hear it... thanks for posting the resolution.

-Dave

---

### Post by mxyzptlk on 2005-11-01
i'm not sure about firestart is the problem.

i just configure a network with an Ubuntu machine as server (samba), 3 XP boxes and one MacOS connected to a router (without samba) an all of the have internet connection.

you have to make sure of some few things

first: try to get the DHCP IP address and the DNS server IP adress of the hotel.

your ubuntu machine has to be like this:

your eth0 configuration ip static, sub.net mask (usually 255.255.255.x) gateway it has to be the DHCP IP address of the  hotel and in DNS (usually is the same as DHCP) make sure you have both the IP and the domain name if not type them there

for firestarter:

preferences-device connected to internet it has to be your eth0,
make sure you have unchecked all the boxes of advanced options and in policies change to "permissive"

you have to activate DHCP for LAN and check the box that says "keep current DHCP configuration" DO NOT CHANGE THE CONFIGURATION THERE

i hope it works



mxyzptlk
the truth will set you free

---

### Post by mrmcctt on 2005-11-02
I may give it a try with Firestarter again but I keep thinking there has to be an easier way to make a DHCP connection.

Trying to discover the DNS and DHCP settings for each new hotel I am going to will get tedious at best.  There has to be something I'm not doing correctly to get this to work.

---

### Post by mrmcctt on 2005-11-02
I think I'm missing something here.  I've done ```
sudo gedit /etc/resolv.conf
``` several times to add the DNS address to this hotel.  I've also gone to Main Menu>System>Administration>Networking and added the DNS address there.

This is just an annoyance really but every time I reboot or power the system back on I have to re-apply the DNS setting to Main Menu>System>Administration>Networking to allow me to connect again.

My resolv.conf file contains these two entries ```
nameserver 168.95.1.1
nameserver 10.59.241.99
```.

I have tried to save the second (which allows me access to the net) but it goes away on reboot or poweroff/on.  I have tried to comment out the first (#) but that didn't work.  If I remove the first and leave the second, when I reboot the first is back and the second disappears.

Any suggestions?  I can do this manually but I like to try to find out why things are doing what they're doing and fix them if possible.

BTW- I did get this all working with Firestarter so I kind of gave it a bad rep before.  It was just that I needed to add the DNS address manually to get everything to work.

As a thought, would this have something to do with the "location" setting in Main Menu>System>Administration>Networking?

---

### Post by mgor on 2005-11-02
dhclient is overwriting it.
this is how to keep it from doing it on netbsd and i guess it's the same in linux.
create /etc/dhclient-enter-hooks and add the following
```
make_resolv_conf() {
}
```

---

