---
title: "setting up web server"
date: 2009-03-01
forum: General Help
---

### Post by SpikeyMike on 2009-03-01
hi, I have installed apache2 and got it working from within my home network, I can now access it using the ip address of the ubuntu pc running apache, I have two problems though, firstly I cannot access it from outside my home network, ie, using my external ip address, when I use that I just see the configuration page for the orange livebox, I have forwarded ports 80 and 443 on the livebox to point to the webserver but it only works from within my home network, the second thing is, the ubuntu pc currently is using dhcp but I wanted to set a static ip address, I did this in the network settings, changing it from dhcp to manual and entering the necessary settings, it works ok until I restart the computer when it reverts back to dhcp. any help appreciated


Spikey

---

### Post by handy on 2009-03-01
You'll attract more help in the Server Platforms sub-forum.

I've asked the mod's to move your thread.

---

### Post by DGortze380 on 2009-03-01
> **SpikeyMike said:**
> hi, I have installed apache2 and got it working from within my home network, I can now access it using the ip address of the ubuntu pc running apache, I have two problems though, firstly I cannot access it from outside my home network, ie, using my external ip address, when I use that I just see the configuration page for the orange livebox, I have forwarded ports 80 and 443 on the livebox to point to the webserver but it only works from within my home network, the second thing is, the ubuntu pc currently is using dhcp but I wanted to set a static ip address, I did this in the network settings, changing it from dhcp to manual and entering the necessary settings, it works ok until I restart the computer when it reverts back to dhcp. any help appreciated


Spikey

You'll have to edit /etc/network/interfaces to have persistent static addresses.

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by bodhi.zazen on 2009-03-01
If you can not access your web server outside you lan, either your router is misconfigured or are you perhaps using a firewall of some kind ? Obviously Apache is working, so it is a matter of configuring your port forwarding and / or firewall.

As far a dhcp, I am guessing you have installed gnome and are using network manager. Network manager does not like to set a static IP, set one in your config files instead.

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

Then disable network manager :

System -> Preferances -> Start up applications Deslelect (uncheck) Network Manager.

---

### Post by handy on 2009-03-02
Looks like the mod's think this thread will do better in General Help for some reason? :confused:

---

### Post by bodhi.zazen on 2009-03-02
> **handy said:**
> Looks like the mod's think this thread will do better in General Help for some reason? :confused:

It appears the question is "general" in that the server is working.

---

### Post by handy on 2009-03-03
> **bodhi.zazen said:**
> It appears the question is "general" in that the server is working.

So you don't think it is easier for those that browse sub-forums to see all related threads in the same area?  Some browse for education, not just to solve other's problems.

---

### Post by SpikeyMike on 2009-03-03
thanks everyone for your replies, I since figured out how to configure the livebox for use with a webserver, I have posted a how-to, this worked for me so I hope it works for others, here it is:

[http://ubuntuforums.org/showthread.php?p=6830613#post6830613](http://ubuntuforums.org/showthread.php?p=6830613#post6830613)

I still have a problem setting a static ip address though, I tried editing /etc/network/interfaces but all that was there was the following:

auto lo
iface lo inet loopback

I deleted this and filled in the following:

auto eth0
iface eth0 inet static
        address 192.168.0.18
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.1

I then restarted the network using:

sudo /etc/init.d/networking restart

but in the terminal it said:

ignoring unknown interface eth0=eth0

and I still have the dynamic ip address

any advice appreciated

Spikey

---

### Post by DGortze380 on 2009-03-03
> **SpikeyMike said:**
> thanks everyone for your replies, I since figured out how to configure the livebox for use with a webserver, I have posted a how-to, this worked for me so I hope it works for others, here it is:

[http://ubuntuforums.org/showthread.php?p=6830613#post6830613](http://ubuntuforums.org/showthread.php?p=6830613#post6830613)

I still have a problem setting a static ip address though, I tried editing /etc/network/interfaces but all that was there was the following:

auto lo
iface lo inet loopback

I deleted this and filled in the following:

auto eth0
iface eth0 inet static
        address 192.168.0.18
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.1

I then restarted the network using:

sudo /etc/init.d/networking restart

but in the terminal it said:

ignoring unknown interface eth0=eth0

and I still have the dynamic ip address

any advice appreciated

Spikey


First, you need to leave those first two lines in /etc/network/interfaces

You've disabled your loopback interface, you'll want that at some point, and some programs depend on it.

Can please post the output of ifconfig -a

You have some kind of syntax error in your /etc/network/interfaces file. Either removing the loopback caused it, or you have the wrong interface listed (ie. eth0 does not exist on your machine)

---

### Post by SpikeyMike on 2009-03-03
> **DGortze380 said:**
> First, you need to leave those first two lines in /etc/network/interfaces

You've disabled your loopback interface, you'll want that at some point, and some programs depend on it.

Can please post the output of ifconfig -a

You have some kind of syntax error in your /etc/network/interfaces file. Either removing the loopback caused it, or you have the wrong interface listed (ie. eth0 does not exist on your machine)

Hi, I realised after that I probably should have left that in and put it back, here is the contents of /etc/network/interfaces as it stands:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
Auto eth0
iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


and here is the output of ifconfig -a:

mikey@Ubuntu:~$ sudo gedit /etc/network/interfaces
mikey@Ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:b9:42:f7  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:feb9:42f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1558413 (1.5 MB)  TX bytes:292483 (292.4 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr ea:ee:25:e3:8d:dd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mikey@Ubuntu:~$ 


thanks

Spikey

---

### Post by DGortze380 on 2009-03-03
> **SpikeyMike said:**
> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
Auto eth0
iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1




Auto in line 6 should be auto

Are you using IPVv6??

verify your interface file looks like above (with a lowercase a), and run again

sudo /etc/init.d/networking restart

let me know the outcome.
I'm out of ideas. I'm confused as to why you have an IPv6 address on eth0 though.

---

### Post by SpikeyMike on 2009-03-04
> **DGortze380 said:**
> Auto in line 6 should be auto

Are you using IPVv6??

verify your interface file looks like above (with a lowercase a), and run again

sudo /etc/init.d/networking restart

let me know the outcome.
I'm out of ideas. I'm confused as to why you have an IPv6 address on eth0 though.

Thanks for your help, what I have done is installed wicd which removes network-manager and I was then able to set a static ip address that stays and doesn't revert back to dhcp. I'm not sure why i had an IPv6 address on eth0, I am not using IPv6 so it is rather confusing.

The only thing i'm not sure about is how to add the gpg authentication in symantec package manager for wicd. What I did was edit /etc/apt/sources.list and add:

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid ibex extras

but when I refreshed symantec package manager I got the following error message:

Failed to fetch [http://apt.wicd.net/dists/intrepid/Release](http://apt.wicd.net/dists/intrepid/Release)  Unable to find expected entry  ibex/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

any ideas what the problem is?

Spikey

---

