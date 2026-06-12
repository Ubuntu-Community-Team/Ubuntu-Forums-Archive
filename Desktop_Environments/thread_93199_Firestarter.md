---
title: "Firestarter"
date: 2005-11-21
forum: Desktop Environments
---

### Post by ace2005 on 2005-11-21
I can't get Firestarter and DHCP to do internet connection shareing for my second computer which is connected via a crossover cable, i've tried installing dhcp but that gives the error described below, tried dhcp3-server and that gives the same error, i set the config in firestarter and it says an unknown error ocurs. Konsole gave this:

> ace@Linux:~$ sudo firestarter
Firewall started
Failed to start DHCP server

With fedora core all i did was give it the ip 192.168.0.1 to the network adapter when i first installed Fedora Core and then in firestarter set the IPs to hand out to from 192.168.0.100 to 192.168.0.105. That was it.

[COLOR="Red"]Can anyone help me set up my network, in any way that makes the internet work apart from changeing the hardware and stuff because the wireing is under the flooring? [/COLOR]

Just internet connection shareing nothing else

---

### Post by arphe_el on 2005-11-22
I type this command as instructed in unofficial ubuntu site

sudo apt-get install firestarter

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

what does it mean?

thank you and GODspeed!

---

### Post by Pablo_Escobar on 2005-11-22
arphe_el - If You're apt-getting , make sure You have Synaptic switched off :)

---

### Post by arphe_el on 2005-11-22
thank you pablo it's now up and running. GODspeed!

---

### Post by ace2005 on 2005-11-22
[QUOTE=arphe_el]thank you pablo it's now up and running. GODspeed![/QUOTE]


Did you get DHCP to work???

---

### Post by ace2005 on 2005-11-23
Great, does anyone care to help?

---

### Post by ace2005 on 2005-11-24
Heeeeeeeelllllllllllllllooooooooooooooo?????

---

### Post by migueljacq on 2005-11-24
Sounds like your DHCP isn't working, but that isn't the be all and end all.
I don't use DHCP, I use static IP addresses for both my computers that are connected via a crossover cable.
When I installed firestarter, I just clicked 'enable internet connection sharing' (NAT) and it all worked.
Your problem might be solved if you just assign static IP addresses to your machines instead of trying to use DHCP.

---

### Post by rx7haze on 2005-12-12
Do you need to set the gateway address on the client pc? I enabled internet connection sharing and set the gateway address on the client pc and it doesn't work. It didn't work without the gateway address either.

---

### Post by runlevel0 on 2005-12-12
I don't know how big your network is, but in case it is a home network (I have 3 boxes and the router), I would strongly suggest setting static IPs... DHCP is a loss of time unless you have a relatively big network.

It could be that DHCP is not running. My first guess would be checking if the daemons are running. Unfortunately, Debianinit scripts do not have a "status" feature, so we will simply try to start them. Debian systems use two daemons, AFAIK, dhcp-server and dhcp-client. I can't stat it as I don't use this software, and in some distros it's called simply dhcpd. But that's no problem as we have TAB-completion in the shell. This command will show you what dhcp deamons are there:

```
 
/etc/init.d/dhcp[TAB]

```

[TAB] means the tabulator key, of course.

To start the deamon (first the server if there is such):

```

sudo /etc/init.d/dhcp-server start

```

This syntax  [color=#33CCFF]/etc/init.d/whatsoever start/stop[/color] can be used to start/stop any daemon. 

If there are errors with your DHCP installation they will show you a message on the shell while trying to start the daemon.

In this case, copy&paste it here.

---

### Post by rx7haze on 2005-12-13
[QUOTE=runlevel0]I don't know how big your network is, but in case it is a home network (I have 3 boxes and the router), I would strongly suggest setting static IPs... DHCP is a loss of time unless you have a relatively big network.

It could be that DHCP is not running. My first guess would be checking if the daemons are running. Unfortunately, Debianinit scripts do not have a "status" feature, so we will simply try to start them. Debian systems use two daemons, AFAIK, dhcp-server and dhcp-client. I can't stat it as I don't use this software, and in some distros it's called simply dhcpd. But that's no problem as we have TAB-completion in the shell. This command will show you what dhcp deamons are there:

```
 
/etc/init.d/dhcp[TAB]

```

[TAB] means the tabulator key, of course.

To start the deamon (first the server if there is such):

```

sudo /etc/init.d/dhcp-server start

```

This syntax  [color=#33CCFF]/etc/init.d/whatsoever start/stop[/color] can be used to start/stop any daemon. 

If there are errors with your DHCP installation they will show you a message on the shell while trying to start the daemon.

In this case, copy&paste it here.[/QUOTE]


Do I need to do this even though I am using static IP addresses?

---

