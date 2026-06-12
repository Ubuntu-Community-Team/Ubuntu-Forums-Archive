---
title: "Can't connect to Internal IP"
date: 2006-10-02
forum: Desktop Environments
---

### Post by random_mike on 2006-10-02
Hi, I have a strange problem that just poped up out of 
nowhere.

I cant't connect to my internal server using the servers internal IP address from my ubuntu computer on the same network only with the external IP or example.com(pointng to my external IP).

My network:

router WAN STATIC IP, LAN 192.168.01.01

ubuntu server, Static 192.168.01.11 IP, running Http, SSH, FTP, SAMBA, webmin

PC1 Windows dhcp 192.168.01.??
PC2 Ubuntu dhcp 192.168.01.??
PC3 Ubuntu/windows dhcp 192.168.01.??

Both PC1 and PC2 work fine so do PC3 when i bot in windowsXP or run the live CD Ubuntu 06. Then i can surf to my http or ssh using my internal IP address, [http://192.168.01.11](http://192.168.01.11), ssh example@192.168.01.11.

I can ping the server with PC3/Ubuntu but not connect using 192.168.01.11. It has worked before but I don't know what happned or what to do.

I've dubble checked the router/server for everything but it must be PC3/Ubuntu that is fault.

Nothing strange in /etc/hosts

PC3 got 2 NICs eth0 and eth1(wireless). Using eth0, eth1 disabled.

DHCP IP on eth0. IP, netmask looks ok. "default gw" looks ok. /etc/resolov.conf looks ok.

I'm so out of ideas, any help would be very appreciated.

---

### Post by wieman01 on 2006-10-02
Have you installed a firewall (e.g. Firestarter) lately?

---

### Post by random_mike on 2006-10-02
Yes I have. Firestarter.
Stoped it, boom problem solved.
How simple... so stupid of me.

Well THANK YOU!!!  :-D

---

### Post by wieman01 on 2006-10-02
> **random_mike said:**
> Yes I have. Firestarter.
Stoped it, boom problem solved.
How simple... so stupid of me.

Well THANK YOU!!!  :-D
Sounds strangely familiar. :-) That's why I was asking...

---

### Post by JohnnyAvocado on 2006-12-09
I have the same exact problem. This is day 2 of Ubuntu for me and I just don't know how to turn off the firewall. I assume the firewall is running by default. Thanks so much for any help.

(BTW, I don't have a GUI installed, just command lining it.)

---

### Post by DaveBorealis on 2006-12-09
> **JohnnyAvocado said:**
> I have the same exact problem. This is day 2 of Ubuntu for me and I just don't know how to turn off the firewall. I assume the firewall is running by default. Thanks so much for any help.

(BTW, I don't have a GUI installed, just command lining it.)

Hello,

Type 'which firestarter' and you'll get the full cli path of the program.  Then type 'man firestarter' and you'll see how to fully use it.

```
sudo /usr/sbin/firestarter --stop
```

That'll turn it off on my system.  Yours is probably similary.

Dave

---

### Post by JohnnyAvocado on 2006-12-09
Dave, thanks a million. I really appreciate it. Everything is working fine.

---

### Post by DaveBorealis on 2006-12-09
> **JohnnyAvocado said:**
> Everything is working fine.

However, one more thing.  When you become familiar with firestarter, fine tune it so you can run your firewall _and_ connect to machines internal to you LAN.  It's been awhile since I ran firestarter from the command line, but I remember it was as easy to configure as the gui version that I'm now using with Ubuntu.

Dave

---

### Post by wieman01 on 2006-12-09
But "Firestarter" should not run by default, or has that changed in Edgy?

---

### Post by DaveBorealis on 2006-12-09
> **wieman01 said:**
> But "Firestarter" should not run by default, or has that changed in Edgy?

That's a good point.  In my '/etc/rc2.d' I have the following:
```
S20firestarter -> ../init.d/firestarter
```
so I assume that it's running when I bootup. Yet if I do a 'ps axx', I don't see anything related to either 'firewall' or iptables.  If I do a 'sudo /init.d/firestarter start', and it returns a message saying that it's starting, I still don't see any process that I can tie to a firewall.

Then when I start 'firestarter' via the gui 'System->Administration->Firestarter', 'ps axx' gives:
```
31750 ?        S      0:00 gksu firestarter
31751 ?        Ssl    0:00 firestarter

```
Guess I don't understand how Ubuntu/Firestarter work.  (I'm used to FreeBSD/ipf and Slackware/iptables.)

Anybody know how this firewall works?
Dave

---

### Post by wieman01 on 2006-12-09
Can you find a symblink in this directory?
> ls -l /etc/rc2.d/*firestarter*
First of all, "firestarter" should not be installed by default. If you have a fresh install, "firestarter" should not be there at all. IP Tables (your Linux firewall) let's pass all traffic by default. So there should not be an issues in the first place.

Firestarter simply configures IP Tables and changes them dynamically as you use the GUI ("gksu firestarter") to set up the rules. So it kind of takes away from user the complexity of writing scripts for IP tables manually. I think this is a good feature.

You find a good documentation [here]("http://www.fs-security.com/docs.php").

---

