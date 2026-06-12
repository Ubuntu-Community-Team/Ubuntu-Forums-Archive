---
title: "How can I add additional IP addresses to a Network Interface?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by seasteve on 2006-02-01
In WinXP we can use the “Advanced...” button in “Internet Protocol (TCP/IP) Properties” to add IP addresses of different subnets.  From what I can tell Ubuntu has the same capability through “aliases”.  

I've read posts explaining how to modify the etc/network/interface file but my file looks different so I'm leery of making the changes.  My hope is someone can explain how to add IP addresses through the Gnome GUI, System>Administration>Networking.

---

### Post by hajk on 2006-02-02
I don't know anything about Windows XP, so I'm at a loss as to what you're trying to do here... Do you have two network interfaces on your computer, e.g. eth0 and eth1, each of them on different subnets? In that case, you need separate "iface" lines in /etc/network/interfaces. Just make sure that there is only a single default route (gateway). If this is not your setup, then you should be clearer about what you want to accomplish (if you want help).

---

### Post by darth_vector on 2006-02-02
you want to edit your /etc/network/interfaces file and have something like this:

```
auto eth0
auto eth0:1

iface eth0 inet static
address 192.168.1.1
netmask ...
...

iface eth0:1 inet static
addres 192.168.14.21
netmask ...
...
```

---

### Post by seasteve on 2006-02-02
[QUOTE=hajk]I don't know anything about Windows XP, so I'm at a loss as to what you're trying to do here... Do you have two network interfaces on your computer, e.g. eth0 and eth1, each of them on different subnets? In that case, you need separate "iface" lines in /etc/network/interfaces. Just make sure that there is only a single default route (gateway). If this is not your setup, then you should be clearer about what you want to accomplish (if you want help).[/QUOTE]

With WinXP you can add additional IP addresses to the SAME interface.  This allows the network connection to communicate on different networks.  For example...

I work for a Wireless ISP.  We use static "routable" IP addresses for client interfaces like PCs and routers.  We use "non-routable" IP addresses for the wireless bridge interfaces.   The non-routable network, 10.0.xxx.xxx, allows connection to any wireless bridge without wasting a routable Internet address.  

With XP I can I can enter IP addresses into 1 interface for BOTH networks allowing me to communicate on both without changing MY IP address.

---

### Post by seasteve on 2006-02-02
[QUOTE=darth_vector]you want to edit your /etc/network/interfaces file and have something like this:

```
auto eth0
auto eth0:1

iface eth0 inet static
address 192.168.1.1
netmask ...
...

iface eth0:1 inet static
addres 192.168.14.21
netmask ...
...
```[/QUOTE]

Thank you for the reply but I was hoping someone could explain how to do this through the Gnome GUI, System>Administration>Networking.

Is this a question I should post on Gnome's forum?

---

### Post by darth_vector on 2006-02-02
the gnome networking gui thing is full of bugs. even changing IP's and DNS settings doenst work well (or didnt a few months ago when i tried it).

its not hard making the changes in the textfile, it gives you more control, and it works.

---

### Post by deBaas on 2006-02-02
[QUOTE=seasteve]In WinXP we can use the “Advanced...” button in “Internet Protocol (TCP/IP) Properties” to add IP addresses of different subnets.  From what I can tell Ubuntu has the same capability through “aliases”.  
[/QUOTE]
Aliases are a total different thing. One Nic can only have ONE IP! Plus the loopback IP 127.0.0.1
No more, no less.

---

### Post by darth_vector on 2006-02-03
a NIC can have multiple IP's bound to it.

---

### Post by Brindled on 2006-02-03
similarly, i need to make this system's ethernet card eth0 the gateway for other cpu's on my network.

here's my setup; i have this computer hooked to the cable modem through usb (eth1), and an ethernet card leading to an 8-switch. the switch inturn networks all the outlying cpus's to mine which is the gateway to the internet.

all things aside, i have been running this setup for some time w/ winXP w/ no troubles. i get a fire in my pants wanting to run ubuntu. now that i have partitioned my xp's drive and installed ubuntu and connected to the internet w/ ubuntu, i no longer can serve up my network using xp. i cant even connect w/ this computer using xp, but i can w/ ubuntu.

any help would be much appreciated, as there are 3 others who are now w/o internet because i wanted to play w/ linux.:( 
please, please, please! i need help!

---

### Post by dcstar on 2006-02-03
[QUOTE=Brindled]similarly, i need to make this system's ethernet card eth0 the gateway for other cpu's on my network.
.......[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by seasteve on 2006-02-03
[QUOTE=darth_vector]the gnome networking gui thing is full of bugs. even changing IP's and DNS settings doenst work well (or didnt a few months ago when i tried it).

its not hard making the changes in the textfile, it gives you more control, and it works.[/QUOTE]

OK...got it...No GUI yet.  I will use the interfaces file.  Thanks much for the help.

After modifying the interfaces file, what are the commands to apply the changes?

---

### Post by dcstar on 2006-02-03
[QUOTE=seasteve]OK...got it...No GUI yet.  I will use the interfaces file.  Thanks much for the help.

After modifying the interfaces file, what are the commands to apply the changes?[/QUOTE]
Try:

sudo /etc/init.d/networking restart

---

### Post by ipatec on 2008-01-05
Hello,
I'm a Linux noob...can you help me solving the following problem.
I have a VPS and I want to add an aditional IP, how can I do this?

---

