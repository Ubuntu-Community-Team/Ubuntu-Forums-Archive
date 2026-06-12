---
title: "Firewall: Problems"
date: 2005-10-16
forum: Desktop Environments
---

### Post by mcz on 2005-10-16
I have installed Guarddog on my Kubuntu 5.10.
If I start the firewall (egal what boxes I checked) I can mot connect to Internet. Only when I stop the firewall a connection is possible.

If I start guarddog from a konsole and then I try to ping a site I get this message:
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

Anyone knows what can I do ?

mcz :confused:

---

### Post by cwaldbieser on 2005-10-16
[QUOTE=mcz]I have installed Guarddog on my Kubuntu 5.10.
If I start the firewall (egal what boxes I checked) I can mot connect to Internet. Only when I stop the firewall a connection is possible.

If I start guarddog from a konsole and then I try to ping a site I get this message:
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

Anyone knows what can I do ?

mcz :confused:[/QUOTE]

It sounds like you have the firewall configured to block your access.    When I first started out using guarddog, I had to go back and re-read the instructions a couple times before I finally got it right.

Have you tried firestarter?  I find that it to be a lot more intuitive for simple home use.

---

### Post by mcz on 2005-10-17
[QUOTE=cwaldbieser]
Have you tried firestarter? [/QUOTE]
Yes, bt with the same results.
I've Guarddogg running on Fedora and Suse without problems. Only with this Kubuntu (5.10 - amd64) it does'nt work 
Can it be a wrong configuration of the ethernet card?

mcz

---

### Post by Takis on 2005-10-17
That means your IP tables are blocking ICMP pings, and the ping command has picked up on it. Your connection should still be working, though. Have you tried web browsing? If it doesn't work, you've probably got one small error in your tables, can you please post the contents of ```
sudo iptables --list
```

---

### Post by mcz on 2005-10-18
The connection seems to be on, but I cann't browsing at all. Here is the listing:

# iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  169.254.6.215        0.0.0.0
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
nicfilt    all  --  anywhere             anywhere
srcfilt    all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
srcfilt    all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
s1         all  --  anywhere             anywhere

Chain f0to1 (4 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state NEW
logdrop    all  --  anywhere             anywhere

Chain f1to0 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:5050 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:telnet state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:5000:5001 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:5000
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ftp state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:www state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:webcache state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8008 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8000 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8888 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:time
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:time state NEW
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4000
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:13223 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp dpt:13223
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:cvspserver state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:xmpp-client state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:5223 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ntp
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ntp state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:5190:5193 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpts:5190:5193
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ldap state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:522 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1503 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1720 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1731 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:1024:65535 state NEW
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpts:1024:65535
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6660:6669 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:smtp state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:1863 state NEW
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:pop3 state NEW
logdrop    all  --  anywhere             anywhere

Chain logaborted (1 references)
target     prot opt source               destination
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED '

Chain logaborted2 (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED '
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain logdrop (4 references)
target     prot opt source               destination
logdrop2   all  --  anywhere             anywhere

Chain logdrop2 (1 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain logreject (0 references)
target     prot opt source               destination
logreject2  all  --  anywhere             anywhere

Chain logreject2 (1 references)
target     prot opt source               destination
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable
DROP       all  --  anywhere             anywhere

Chain nicfilt (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere
logdrop    all  --  anywhere             anywhere

Chain s0 (1 references)
target     prot opt source               destination
f0to1      all  --  anywhere             169.254.6.215
f0to1      all  --  anywhere             0.0.0.0
f0to1      all  --  anywhere             localhost.localdomain
f0to1      all  --  anywhere             87.1.77.119
logdrop    all  --  anywhere             anywhere

Chain s1 (1 references)
target     prot opt source               destination
f1to0      all  --  anywhere             anywhere

Chain srcfilt (2 references)
target     prot opt source               destination
s0         all  --  anywhere             anywhere

mcz

---

### Post by Takis on 2005-10-18
Run this command to fix this:
```
sudo iptables -A OUTPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT
```
In English, this command means append to the IP chain/table OUTPUT rules. If you get a packet that uses the ICMP protocol, and its ICMP type is an echo request (ping), and it's new (this bit may have been a bit redundant, but the principle of knowing the state of the packets you want to send through is important) jump to the ACCEPT chain/table (which immediately pushes the packet through).

I don't really know where you could put this to run it every time you reboot your box, though. Maybe there's an entry in /etc/rcS.d that starts GuardDog? If so, could you please post it up and I'll try to show you where you can put this line rather than have to run it every time you reboot.

---

### Post by mcz on 2005-10-19
Thank you, but it does'nt work.

mcz

---

### Post by HermanAB on 2005-10-19
Change the -A to a -I and try again.

The rule needs to be inserted in the beginning, doesn't help if it is appended at the end.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by GeneralZod on 2005-10-19
I know that guarddog on 5.10 by default blocks access to pretty much everything - even ping.  It can be easily re-enabled by re-opening guarddog, going to Protocols, then set ping in Network(?) to Accept.  If you haven't done this step and clicked Apply, then ping will not work.

---

### Post by Takis on 2005-10-19
[QUOTE=HermanAB]Change the -A to a -I and try again.

The rule needs to be inserted in the beginning, doesn't help if it is appended at the end.[/QUOTE]
Oooh yeah I didn't realise where all the rest of the packets were going at the end of OUTPUT. #-o

---

### Post by mcz on 2005-10-21
I changed ta -A to -I and I was able to ping (but only with the 'ping' check box checked in Guarddog). Browsing is still impossible.

Thank,

mcz :p

---

### Post by Takis on 2005-10-25
Hmm that's weird, cause your IP tables seem to show that HTTP should be going through:
> ACCEPT tcp -- anywhere anywhere tcp spts:1024:5999 dpt:www state NEWSo you can browse if you turn off GuardDog?

---

