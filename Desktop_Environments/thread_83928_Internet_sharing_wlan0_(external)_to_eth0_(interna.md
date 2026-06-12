---
title: "Internet sharing wlan0 (external) to eth0 (internal)"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Neobuntu on 2005-10-29
I have a notebook computer (Ubuntu Breezy, new install) that needs updating at my desk where I only have wireless Internet coming in (Ubuntu Breezy) to my desktop computer. I want to work in my computer room and not stand over the access point or drop a cat5 cable. 

With that OTHER (largely crappy) OS, I run the network wizard selecting my wireless card as the Internet connection, and share to my hardwired LAN card set to static address and feeding DHCP to another computer with crossover cable (or into Router WAN port with regular cable and then regular cable out to any box looking for DHCP hook up.) So, ubuntu can do this too, right?

I have searched, read, and tried many things. Maybe I'm missing something obvious but how do you get this done? The closest I have come is with Firestarter.

Firestarter seemed to be the deal! Compleate with wizard that I'd say is the easiest. Firewall, done but sharing is not working. :( It says unknown error check network connection which seems all good. Internet works. eth0 is active and 192.168.0.1.

Firestarter has an easy check box for sharing. Why doesn't it work? Can it not go from wlan0 to eth0? I even tried inserting a bridge command into "Interfaces" with no change. What does one do here? I can not get the eth0 to serve DHCP to save my life.

Also, the network setting in Gnome "Networking" for the eth0 gateway needs to stay blank, right? I tried all the gateways involved (below) just to be sure.

Also, my subnets are correct because they work with the other OS. One has to make sure they are different per gateway/router. 192.168.1.1 (The AP), 192.168.0.1 sharing gateway computer eth0, and if I don't use a direct crossover, I can go to the last router as 192.168.2.1. All this worked, just not with Ubuntu for me yet.

Please help?

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=Neobuntu]I have a notebook computer (Ubuntu Breezy, new install) that needs updating at my desk where I only have wireless Internet coming in (Ubuntu Breezy) to my desktop computer. I want to work in my computer room and not stand over the access point or drop a cat5 cable. 

With that OTHER (largely crappy) OS, I run the network wizard selecting my wireless card as the Internet connection, and share to my hardwired LAN card set to static address and feeding DHCP to another computer with crossover cable (or into Router WAN port with regular cable and then regular cable out to any box looking for DHCP hook up.) So, ubuntu can do this too, right?

I have searched, read, and tried many things. Maybe I'm missing something obvious but how do you get this done? The closest I have come is with Firestarter.

Firestarter seemed to be the deal! Compleate with wizard that I'd say is the easiest. Firewall, done but sharing is not working. :( It says unknown error check network connection which seems all good. Internet works. eth0 is active and 192.168.0.1.

Firestarter has an easy check box for sharing. Why doesn't it work? Can it not go from wlan0 to eth0? I even tried inserting a bridge command into "Interfaces" with no change. What does one do here? I can not get the eth0 to serve DHCP to save my life.

Also, the network setting in Gnome "Networking" for the eth0 gateway needs to stay blank, right? I tried all the gateways involved (below) just to be sure.

Also, my subnets are correct because they work with the other OS. One has to make sure they are different per gateway/router. 192.168.1.1 (The AP), 192.168.0.1 sharing gateway computer eth0, and if I don't use a direct crossover, I can go to the last router as 192.168.2.1. All this worked, just not with Ubuntu for me yet.

Please help?[/QUOTE]
Firestarter is supposed to do Internet Connection sharing for you.  If that isn't working, you can use iptables to manually turn your one of your computers into a router (which is what it seems like you are trying to do, if I am reading your synopsis correctly).  If you need help understanding how to configure iptables to do this I can try to help you set up a simple script to do it.

---

### Post by Neobuntu on 2005-10-30
Yes thank you, that is what I am in effect trying to do. I would like my desktop to (on comand) share my incoming wireless Internet to the hard eth0, cat5 out for my notebook and other computers where I am installing and upgrading Ubuntu. I am conserned about security on my desktop/sharing/gatway while in operation. 

I suppose Firestarter would handle the firewalling if the sharing worked. I would like to know why Firestater isn't working or at least without more information from Firestarter as to why? (define the problem)

Since Firestarter is a frount end I would like to know about the script you mention.

Anyone else replicate this Firestarter problem? I found no solution searching Firestarter. (I also tried guidedog with no luck)

---

### Post by Neobuntu on 2005-10-30
Aaaaah!  What's the secret here? 

I found a reference to Firestarter NOT having a dhcp server and recomending dhcp which I installed but it didn't work so I uninstalled it and noticed ubuntu has it's own dhcp3 server (ahh) which seemed to be a match but after installing it, Firestarter still doesn't share (server dhcp.) 

What am I doing wrong? I would really like to resolve this and leave a trail for other to follow. I am at a loss.

Checked all connections. 
Checked that eth0 is active.
Connected cross over cable (eth0) directly to client notebook (which has no problem as a client to another system).
Did network restart till my eyes are falling out.

Don't get me wrong here Ubuntu is the tip top best of all but this sucks.

---

### Post by cwaldbieser on 2005-10-30
[QUOTE=Neobuntu]Yes thank you, that is what I am in effect trying to do. I would like my desktop to (on comand) share my incoming wireless Internet to the hard eth0, cat5 out for my notebook and other computers where I am installing and upgrading Ubuntu. I am conserned about security on my desktop/sharing/gatway while in operation. 

I suppose Firestarter would handle the firewalling if the sharing worked. I would like to know why Firestater isn't working or at least without more information from Firestarter as to why? (define the problem)

Since Firestarter is a frount end I would like to know about the script you mention.

Anyone else replicate this Firestarter problem? I found no solution searching Firestarter. (I also tried guidedog with no luck)[/QUOTE]

Well, what you are looking to do is called Network Address Translation (NAT).  Basically, what will happen is that one machine (the router) will take all the outgoing requests from the network it represents and send them out to the network it is routing to (in typical cases, that network is the Internet).  From the outside network's point of view, it is only dealing with the router.  However, the router tracks the connections, and it alters the packets being sent/received so they go to the correct computers.

DHCP and DNS are seperate issues, but you usually need to deal with them in some way to achieve a simple-to-use network.

Is there some reason you want to use DHCP?  For a small home network, it can sometimes be easier to just set up static IP addresses than it is to set up your own DHCP server.  If you do want to use DHCP, you are correct that Ubuntu has its own DHCP server that you can install.  You will probably have to configure it somewhat, and I will admit right off the bat that I've never done that before, so my help in that regard may be limited.

As far as a script to set up NAT goes:
+ First we start by making a simple script to issue the necessary commands.  If you have never made a bash script before, it is really easy.  You just make a text file called something like "router.sh" (you can use gedit, or vi or nano or whatever editor you like).  The top line should look like:
```

#!/bin/bash

```
This just tells the script that the bash shell is the program that is supposed to run it.  You then change the permissions on the file and turn the execute permissions on for yourself.

Every line you enter in the file starting with "#" is a comment, so you can type information that helps you remember later why you did something.
Without getting into more advanced stuff, the other lines are just commands that you would normally just type in at the terminal.  They get run in order.

The command you will use to set up NAT is called "iptables".  It has a boatload of configuration options, but we are going to use just a tiny subset.

Since iptables is front end to Netfilter, just like firestarter or guarddog/guidedog, you will probably want to disable those programs while you are trying out your script.

OK, here is the really basic script.  I will assume your wireless card is wlan0.  I will also assume wlan0 is IP address 192.168.0.2 on a 192.168.0.0/24 network.  Your local network will be assumed to be a 192.168.1.0/24 network:
```


#Enable IP Forwarding
sudo bash -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

#Clear all NAT rules.
sudo iptables -t nat -F
#Enable NAT
#In English-- Take the packets that originate from the 192.168.1.0/255.255.255.0 network and are going to be routed the wlan0 card, and change them so it looks like the IP address they came from *is* the wlan0 IP address.
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/255.255.255.0 -o wlan0 -j SNAT --to-source 192.168.0.2

```

So it's basically just two commands, but the iptables one is a little confusing (I always keep a little reference manual handy).

It does assume that your routing table is set up correctly (your laptop wouldn't be able to interact with the Internet / other computers if your routes weren't correct).  It also assumes that you set up your other computers to use your laptop as their default gateway.  If you are not sure how to do that, let me know.

This example also assumes you just set up static IPs for the other computers.  If you are using dynamic IPs, the command has to change slightly-- instead of the SNAT part of the command, it uses something called MASQ.  You could, in theory, always use MASQ, but you get better performance using the right one for the right situation.

---

### Post by Neobuntu on 2005-11-01
I tried that script without Firestarter installed and I tried simply statically setting up the notebook (client shared to) and still no Internet.

I was able to ping back through the desktop (gateway) to the first router(wireless AP) and even log into it. I still don't know why then the Internet doesn't come through. Maybe something with DNS, I don't know.

Again working backwards...

Ubuntu notebook end client is set to 192.168.0.2
LAN static ethernet NIC on my Ubuntu desktop is 192.168.0.1
The wireless card also in the above desktop is (DHCP) 192.168.1.7
Then the Wireless router is 192.168.1.1 NAT DHCP to what ever the ISP assigns.

Ping on the notebook all the way to router 192.168.1.1 is good.
Internet (thus upgrading the notebook) still doesn't work.

---

### Post by mxyzptlk on 2005-11-01
maybe this will help you

in the machine you have the wlan adapter

first: in system-administration.network

your wlan0 must be your default internet gateway, ip assigned by DHCP, check for your essid, check for your key (i suggest hexadecimal) and of course activated.

second: same path.

your eth0 must be like this:
static IP, sub-net mask (usually 255.255.255.0) and (very important) gateway address it has to be the same of your DHCP.

for the firestart:

i think you already use the wizzard

in preferences-network configuration make sure you have checked both boxes activate internet sharing and activate DHCP for LAN DO NOT SELECT CREATE A NEW DHCP CONFIGURATION, let it as "keep current configuration".

also make sure in advanced options you uncheck all the boxes there and check the option "discard slightly" (in reject packages method)

in policy make sure you select "permissive"


now for the other box

lets go to system-administration-network

for the eth0

it has to be like this

static ip (lets say that in the other box your eth0 is 192.168.0.1 so in this one use something like 192.168.0.100 DO NOT CHOOSE WHATEVER YOU WANT) subnet mask 255.255.255.0 and VERY IMPORTANT you have to set a default gateway and it has to be your IP for the eth0 of the first computer the one with the wireless in this example it would be 198.162.0.1

and VERY IMPORTANT again dont forget the DNS it has to be the same of your DHCP IP. 

i did like i just describe for a whole network 

in my case is like this

3 XP boxes and one MacOS connected to a router, and this machine is Ubuntu Breezzy, here i have the internet sharing its a wireless usb adapter the etho is connected to the router also and everything works all boxes have internet



mxyzptlk
the truth will set you free

---

### Post by Neobuntu on 2005-11-02
Hey thank you. It's working!

I think it was a matter of putting the first router in as gateway 129.168.1.1 for the (eth0 192.168.0.1) local NIC setting on the desktop (made gateway) and making sure wlan0 was the default. As you said I already had the CLIENT end notebook set to 192.168.0.1 for GATEWAY (and address 192.168.0.100 is now used instead of 192.168.0.2 but I'm not sure that made a difference.) 

Ah, I see that it would if I were using DHCP (for the local too) via Firestarter. Firestarters default range was 192.168.0.100 and up.)

Which brings me to the fact that instead of dealing with which dhcp (server) has been known to work (lack of help)  I decided it might be simpler to set the local up static (since the nic on the desk top need to be static 192.168.0.1 anyway.) 

Therefore I was able to ping via Firestarters connection sharing setup (like I did with the manual script) and this is much preferable. Firestarter is cool. It's easy to turn on and off. Apparantly it firewalls during the connection sharing so that's a big simple security plus.

Thus since Firestarter stoped (now that all is set as you said) giving me the error and is good to go, now I figured it was just a matter of not having DNS on the static client so I copied the info from DNS and such from the desktop manually to the client notebook and I was able to surf and update Ubuntu. Success!

What I don't yet know is if I install dhcp3 (I think) and run the Firestarter wizard again (and set the notebook NIC to DHCP) if that would work.

In any case, the XP pro (updated) ICS wizard did it all (once you learn the wizard.) Of course Windows overall sucks! I just hope Firestarter can include more clues and automation for the Windows converts. 

Speaking of overall, I'm a heck of a lot more happy with the security and options with open source and my favorite is still Breezy.

AT least Sony isn't changing the freaking Kernel when I listen to a CD! That's in fact what they are doing with Windows.

---

### Post by Neobuntu on 2005-11-02
OK! I tried installing both dhcp3-server and dhcp (with server) each exclusively and running the Firestarter wizard with various settings for each NIC (desktop and client box) and we're back to the same Firestarter errors to load the "firewall."

So I set everything back (time wasted) and I'm good to go with static client set up with manual DNS and stuff typed in.

The only real disadvantage is, now I can't let each client box just log on with DHCP. I have to set each one "correctly" and then put it back to DHCP when I'm done. How much is my time worth anyway? If you hadn't guessed, I'm big on time savings.

So what's the deal with some kind of DHCP server and Firestarter. It's nice but that would have to include WORKING and a fast easy way (Instructions some where) to set this up in Breezy (dhcp served).

I hear you out there, saying "go back to Windows" (not anyone in the Ubuntu forum). Well no. We need to make this easier. 

Leave no benefit behind!

I would be very thankful if you have a fast solution or any DHCP serving and Firestarter experience.

---

