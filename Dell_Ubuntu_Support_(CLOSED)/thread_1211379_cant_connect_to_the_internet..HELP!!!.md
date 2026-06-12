---
title: "cant connect to the internet..HELP!!!"
date: 2009-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by carsonrose on 2009-07-12
I am EXTREMELY new to Linux... that being said, I am a very experienced windows user. I installed Ubuntu 9.04 on one of my dell Optiplex GX270 machines... works great. That is unless I want to use the internet... At my office, I have a network that I connect to, I entered the IP address manually, all went well. I bring this same machine home, no firewall, just plugged into a switch... and this thing REFUSES to get online....I have tried everything.. HELP!!?!?!?!

---

### Post by issih on 2009-07-12
By switch I presume you mean a router of some form (the distinction is pretty technical, but generally routers perform NAT and routing to provide internet access to all machines connected to them, whereas a switch technically just connects different network segments and routes between them)

Anyway, if I am right that you are referrring to something that is acting as a router for your internet connection, how does it assign ip addresses?

Unless the IP setup matches exactly with that at your office I would not expect a manual configuration for one place to work at another.

Chances are that you are using dhcp to automatically assign IP addresses at home, and consequently all you need to do is add a new connection in network manager and set it to use dhcp, then select that connection as the active one.

Hope that helps

---

### Post by carsonrose on 2009-07-12
> **issih said:**
> By switch I presume you mean a router of some form (the distinction is pretty technical, but generally routers perform NAT and routing to provide internet access to all machines connected to them, whereas a switch technically just connects different network segments and routes between them)

Anyway, if I am right that you are referrring to something that is acting as a router for your internet connection, how does it assign ip addresses?

Unless the IP setup matches exactly with that at your office I would not expect a manual configuration for one place to work at another.

Chances are that you are using dhcp to automatically assign IP addresses at home, and consequently all you need to do is add a new connection in network manager and set it to use dhcp, then select that connection as the active one.

Hope that helps

I dont have a routher, its an actual switch... 24 port switch to be exact... so you are saying to add another wired connection? then just set it to auto DHCP? I just did that and there is no change... it searchs for a connection and the tells me "disconnected you are offline"

---

### Post by carsonrose on 2009-07-12
there is nothing doing the DHCP on my side... at the office, there is.. my router/firewall is doing the DHCP... but here at home its motorola cable modem to switch, computer(s) to switch.. windows maching is online just fine.. (the one i am using right now) Ubuntu refuses to do anything except tell me im offline

---

### Post by issih on 2009-07-12
Hmmmn..unless your cable modem or your switch itself has a built in NAT system then that is just not going to work.

You can only connect more than one machine to a single internet connection (where the isp assigns you one single WAN IP address) if you have something performing NAT so that all the machines on the LAN appear to the external world as being one machine.

Its very possible that your switch (clearly being a pro level product) does have the capability to perform NAT if configured correctly, but thats not something I can really help with. Same goes for your modem, it might be capable of doing it, but typically they can't. You have to have a cable modem hooked up to a cable router performing NAT.

Same goes for dhcp really, the router or the switch might well be doing it, but I can't answer that...but probably you can, for a start how is the windows pc set up? how does it get its IP address?

If you are sure that NAT is working, and that DHCP is not, then just manually configure the 2nd ethernet connections ip settings to match the windows pc...i.e. same subnet mask, same default gateway, same dns servers and an ip address that is the same except for the last digit (assuming your subnet mask is 255.255.255.0)

If none of that works you are going to have to assume that your switch/modem are not configured correctly. in which case start by connecting the pc directly to the modem and seeing if that works and then working backwards

---

### Post by carsonrose on 2009-07-12
> **issih said:**
> Hmmmn..unless your cable modem or your switch itself has a built in NAT system then that is just not going to work.

You can only connect more than one machine to a single internet connection (where the isp assigns you one single WAN IP address) if you have something performing NAT so that all the machines on the LAN appear to the external world as being one machine.

Its very possible that your switch (clearly being a pro level product) does have the capability to perform NAT if configured correctly, but thats not something I can really help with. Same goes for your modem, it might be capable of doing it, but typically they can't. You have to have a cable modem hooked up to a cable router performing NAT.

Same goes for dhcp really, the router or the switch might well be doing it, but I can't answer that...but probably you can, for a start how is the windows pc set up? how does it get its IP address?

If you are sure that NAT is working, and that DHCP is not, then just manually configure the 2nd ethernet connections ip settings to match the windows pc...i.e. same subnet mask, same default gateway, same dns servers and an ip address that is the same except for the last digit (assuming your subnet mask is 255.255.255.0)

If none of that works you are going to have to assume that your switch/modem are not configured correctly. in which case start by connecting the pc directly to the modem and seeing if that works and then working backwards

In doing that, it now says that I am connected, but Istill cant surf the web?

---

### Post by issih on 2009-07-12
Doing what?
Connecting to the modem directly?
Setting the IP manually?

The former is more serious, although not necessarily terminal, whereas the latter as I said just means your network configuration is wrong.

Please can you tell me how your windows machine acquires its ip, and what its address is.

what is the IP address you are assigning? if it isn't  something like 192.168.X.X or 10.0.X.X then chances are you are trying to assign WAN ip addresses to your machine, which is not a good idea. I don't really know how that could be working through the switch to the windows box, if that is the case, unlesss it is picking it up via dhcp from the modem (Some modems have limited dhcp designed to provide one, and only one ip address)

---

### Post by carsonrose on 2009-07-12
> **issih said:**
> Doing what?
Connecting to the modem directly?
Setting the IP manually?

The former is more serious, although not necessarily terminal, whereas the latter as I said just means your network configuration is wrong.

Please can you tell me how your windows machine acquires its ip, and what its address is.

what is the IP address you are assigning? if it isn't  something like 192.168.X.X or 10.0.X.X then chances are you are trying to assign WAN ip addresses to your machine, which is not a good idea. I don't really know how that could be working through the switch to the windows box, if that is the case, unlesss it is picking it up via dhcp from the modem (Some modems have limited dhcp designed to provide one, and only one ip address)

1. i tried skipping the switch and plugging it in directly from the modem, no change. 
2. I tried to manually assign the IP address, both through the switch and directly.. says Im not connected, but still cannot surf the web. 

I assigned the IP directly as i saw it in windows. here is a screen shot: (it wont let me add the screen shot for whatever reason.)

I guess i dontknow how to answer your question about how windows connects, other than i just plug it in and it found the connection and just worked.
[IMG]file:///C:/DOCUME%7E1/Brandon/LOCALS%7E1/Temp/moz-screenshot-2.jpg[/IMG]
[IMG]file:///C:/DOCUME%7E1/Brandon/LOCALS%7E1/Temp/moz-screenshot-1.jpg[/IMG]
[IMG]file:///C:/DOCUME%7E1/Brandon/LOCALS%7E1/Temp/moz-screenshot-3.jpg[/IMG][IMG]file:///C:/DOCUME%7E1/Brandon/LOCALS%7E1/Temp/moz-screenshot-4.jpg[/IMG]

---

### Post by carsonrose on 2009-07-12
[IMG]file:///C:/DOCUME%7E1/Brandon/LOCALS%7E1/Temp/moz-screenshot-5.jpg[/IMG]

---

### Post by issih on 2009-07-12
Ok, from that I can tell you that your windows machine is picking up its IP address using dhcp, and that it is picking up a WAN ip address (i.e. one assigned by your ISP) that is publicly accessible from the internet.

Consequently setting your ubuntu machine's IP manually is pointless, as you will almost certainly only be allowed one WAN IP by your ISP, and it will reject the other one.

You will not be able to have two machines connected to the modem with the equipment you have now, unless your switch is capable of performing NAT as I mentioned earlier. You will need to purchase a cable router.

From now on I am assuming you are connecting directly to the modem.....

AS for connecting directly to the modem, you need to try connecting the ubuntu box directly to the modem with it set to use DHCP to acquire its IP address. Ensuring that you have activated (selected in the network applets dropdown list) the connection you have set to use dhcp, and not any of the others you may have made during this process.

Once you have done that right click on the networking applet and select connection information. The dynamically acquired IP address should look very similar to the one the windows box had, and hopefully you will have internet access.

If you can't connect in that scenario, then your ISP is most likely one of the cable companies that locks the mac address of the machine that can connect to the modem. That is to say that unique hardware address (mac address) of the network card in your windows pc has been stored, and from now on the only machine that your isp will let connect through your modem is one that has that mac address..This is not uncommon.

To test if this is what is stopping you getting any connection, you will need to issue the following commands in a terminal (Applications->Accessories->Terminal)

```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:0F:1F:8F:35:E8
sudo ifconfig eth0 up

```

N.B. enter your login password when prompted..

These commands "spoof" your mac address so that its hardware address matches that of your windows computer. If you can connect only after issuing these commands then your modem is locked to one mac address. Note that I have read your windows mac address (00:0F:1F:8F:35:E8 ) from your screenshot, which is a bit blurry, so do check it first.

---

### Post by carsonrose on 2009-07-12
tried that and two things:

1. when entering the HW line, it says 'unknown Host'
2. still doesn't work when auto DHCP and plugged directly from modem to box
3. Cant be the issue because I can connect with my laptop if i plug directly in... or my desktop when plugged directly in...

---

### Post by issih on 2009-07-12
Agreed, if you can connect your laptop or main windows box directly to the modem and get internet access then the mac address shouldn't be the issue.

What does connection information say your IP address is when the ubuntu box is connected directly to the modem with dhcp turned on?

Assuming you have got a sensible looking IP address then you really should have internet access, just to check whether somehoew this is a dns issue rather than a dhcp one can you open a terminal once the box is hooked up and try the following command:

```
ping 209.85.229.104
```

N.B. hit ctrl-c to end the program.

does that give you ping times or just report "no route to host"?

if its the former, then you are actually connected to the internet, and we have a dns issue.


OOH - just a thought, if you have created a new connection, and that connection is the one that you have set up with dhcp, have you set the mac address of the interface it relates to?

In the first tab ("Wired") of the dialog that editing the connection brings up there is a space for the mac address, copy over the value that is present in the original connections mac address field into there... shouldn't matter with only one ethernet card I don't think, but I'm not sure

---

### Post by carsonrose on 2009-07-12
> **issih said:**
> Agreed, if you can connect your laptop or main windows box directly to the modem and get internet access then the mac address shouldn't be the issue.

What does connection information say your IP address is when the ubuntu box is connected directly to the modem with dhcp turned on?

Assuming you have got a sensible looking IP address then you really should have internet access, just to check whether somehoew this is a dns issue rather than a dhcp one can you open a terminal once the box is hooked up and try the following command:

```
ping 209.85.229.104
```N.B. hit ctrl-c to end the program.

does that give you ping times or just report "no route to host"?

if its the former, then you are actually connected to the internet, and we have a dns issue.



OOH - just a thought, if you have created a new connection, and that connection is the one that you have set up with dhcp, have you set the mac address of the interface it relates to?

In the first tab ("Wired") of the dialog that editing the connection brings up there is a space for the mac address, copy over the value that is present in the original connections mac address field into there... shouldn't matter with only one ethernet card I don't think, but I'm not sure

Ipv4 has no IP address at all... there fore cant ping anything... has been the main issue with auto dhcp from the beginning... :(

---

### Post by issih on 2009-07-12
If you have the ubuntu box connected directly to the modem and it is meant to be using dhcp then you have a very small number of things you can affect, it should be pretty much automatic.

Double and Triple check you interface set up.

I.E go into edit connections and delete ALL the wired connections except one so you know for certain what is happening..now edit your one remaining connection.

tick the box to have it automatically connect

On the "Wired" tab
Set the Mac address to your ethernet cards mac address.
Set the MTU drop down to "automatic" (which is 0).

On the 802.1x tab
ensure the top box is unticked and everything else is greyed out.

On the IPv4 tab
select "Automatic (DHCP)" from the method drop down

Now hit apply.

Now when you left click on the network manager applet there should be just that one connection listed, and it obviously should be selected.

hopefully that should connect, if not then something odd is going on, or your modem has some specific setup features like a mac filter that you are not aware of

---

### Post by carsonrose on 2009-07-12
Still.......no change... Im beginning to think that perhaps Ubuntu was a mistake to install..

The same machines with Windows got online just fine, its when i installed Ubuntu that the breakdown happened. :(

And thats really too bad to, because Ubuntu works just fine at my office. This only leaves me to think that its something in the DHCP that is screwing up here.... The router/firewall at my office does the DHCP, so when i set Ubuntu static, it just works... but I have been trying to get this to work for 3 days now and still at square one at home...

---

### Post by issih on 2009-07-12
Something odd is happening, from what you have told me, dhcp connected to the modem should work.

Having sid that, your understading of what dhcp is seems to be a bit wrong.

dhcp stands for dynamic host control protocol. It is a technology designed so that when a machine is plugged into a network it is automatically detected, assigned an IP address and subnet mask so that other machines on the network can see it (and vice versa) and has the ip address of the default gateway and dns server assigned (usually both of these are the cable/adsl router's ip).

This is all done automatically, you just plug the wire in and it works.

By setting a manual ip address for use in your office you are explicitly NOT using DHCP. Instead you are supplying all the above parameters manually.

From what you have shown me, the windows machines on your home network are connecting to your modem via dhcp, theoretically ubuntu with dhcp set up should just work. You have something odd going on.

I am about out of ideas, but one last roll of the dice, what output do you get if you try running:
```
sudo dhclient eth0
```

in a terminal whilst connected to the modem?

---

### Post by dryfyre on 2009-07-12
try going to the network tools under system

---

### Post by carsonrose on 2010-07-14
> **issih said:**
> Ok, from that I can tell you that your windows machine is picking up its IP address using dhcp, and that it is picking up a WAN ip address (i.e. one assigned by your ISP) that is publicly accessible from the internet.

Consequently setting your ubuntu machine's IP manually is pointless, as you will almost certainly only be allowed one WAN IP by your ISP, and it will reject the other one.

You will not be able to have two machines connected to the modem with the equipment you have now, unless your switch is capable of performing NAT as I mentioned earlier. You will need to purchase a cable router.

From now on I am assuming you are connecting directly to the modem.....

AS for connecting directly to the modem, you need to try connecting the ubuntu box directly to the modem with it set to use DHCP to acquire its IP address. Ensuring that you have activated (selected in the network applets dropdown list) the connection you have set to use dhcp, and not any of the others you may have made during this process.

Once you have done that right click on the networking applet and select connection information. The dynamically acquired IP address should look very similar to the one the windows box had, and hopefully you will have internet access.

If you can't connect in that scenario, then your ISP is most likely one of the cable companies that locks the mac address of the machine that can connect to the modem. That is to say that unique hardware address (mac address) of the network card in your windows pc has been stored, and from now on the only machine that your isp will let connect through your modem is one that has that mac address..This is not uncommon.

To test if this is what is stopping you getting any connection, you will need to issue the following commands in a terminal (Applications->Accessories->Terminal)

```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:0F:1F:8F:35:E8
sudo ifconfig eth0 up

```N.B. enter your login password when prompted..

These commands "spoof" your mac address so that its hardware address matches that of your windows computer. If you can connect only after issuing these commands then your modem is locked to one mac address. Note that I have read your windows mac address (00:0F:1F:8F:35:E8 ) from your screenshot, which is a bit blurry, so do check it first.

Im not sure what I did to fix this, but goign through my old posts i found this...... but thanks for your help anyway!

---

