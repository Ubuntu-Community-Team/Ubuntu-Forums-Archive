---
title: "Xbox Live &quot;NAT Moderate&quot; issue: SOLVED!"
date: 2007-08-30
forum: Gaming &amp; Leisure
---

### Post by FRuMMaGe on 2007-08-30
Many people who own an Xbox 360 and don't want to shell out for the wireless adapter have used an ethernet cable to connect to their laptop or desktop computer in order to access Xbox Live.  However, many people have found that after they have finished setting up the correct ip routing configuration they are recieving a message saying their NAT is set to "Moderate", when it should be "Open".

The problem with the moderate setting is that you cannot access some games online and you may not be able to hear the teamspeak of other users.

After searching the forums to find a solution for this problem, I resorted to look on some Micro$oft forums.  I managed to adapt the windows solution to work with linux (easily).  All you have to do is forward ports 88 and 3074 to ports 88 and 3074 on the Xbox!

This is particularly easy if you use Firestarter:
[IMG]http://img213.imageshack.us/img213/1555/firerk4.png[/IMG]

I hope this helps people who were having the same problem as me.

---

### Post by gnatwest on 2008-02-03
Ive done this and still get a moderate NAT.  I havent noticed a degradation of service because of it though.

---

### Post by Rogers on 2008-03-01
> **gnatwest said:**
> Ive done this and still get a moderate NAT.  I havent noticed a degradation of service because of it though.

Same here, must of changed it.

---

### Post by Rogers on 2008-03-02
Bump..... anyone managed to get this thing into open mode on the new XBOX live release?

---

### Post by DeVonne on 2008-05-16
Thank YOU!!!

For the longest time ubuntu said moderate now it is open

However my xbox said it was 192.168.0.3 so I changed 192.168.1.2 to the IP of the xbox and it worked

:D thanks!

---

### Post by Jovec on 2008-05-16
This would only work if your Linux computer is acting as your NAT router.  For those whom this doesn't work are you running your 360 and other computers through a dedicated router?  You would have to configure that router to forward the ports appropriately.

---

### Post by Xecuter on 2008-08-09
I don't wanna install firestarter, how do i do it with iptables?

---

### Post by pmcchapman on 2008-12-29
My Christmas present to myself was an Xbox 360, unwilling to pay the crazy asking price for an official wireless adapter, i did the following, which solved the moderate issues (no messenger) for me - hope it helps those still struggling.

The full set of ports that need to be opened for Xbox live to work are:

TCP 80
UDP 88
UDP 3074
TCP 3074
UDP 53
TCP 53

[http://support.xbox.com/support/en/us/xbox360/kb.aspx?ID=908874&lcid=1033&category=live]("http://support.xbox.com/support/en/us/xbox360/kb.aspx?ID=908874&lcid=1033&category=live")

For my set up, I am using my PC to connect via wireless to my router, then connecting my xbox with a **crossover cable** to the ethernet connection on my PC. I have:

Installed Firestarter (cheating I know, but made life so very simple, plus it is in Ubuntu's 'Add/Remove' so it was a no-brainer)

Enabled internet sharing in Firestarter, with wlan0 as connected to the internet, and eth0 as the internal network. DHCP not enabled, as I am happy to give the Xbox static IP.

Assigned my eth0 as 192.169.0.1 / 255.255.255.0 (system - preferences - network configuration)

Connected ethernet to my Xbox 360 which I have assigned the following static details - 192.168.0.2 / 255.255.255.0 / 192.168.0.1 and the DNS lookups as reported by the following terminal command:
[INDENT][/INDENT]gedit /etc/resolv.conf

How to do all of the above is detailed here:

[http://www.fs-security.com/docs/connection-sharing.php]("http://www.fs-security.com/docs/connection-sharing.php")

Doing all of the above got me connected to live, but with only moderate connectivity. I then assigned my wireless a static address outside the routers DHCP range (system - preferences - network configuration), and then manually opened the six ports detailed above using the routers own management tool. I then added the details to Firestarter's inbound policy as shown in the attachment to this post.

(NB: I realised after a bit of trial and error that Ubuntu defualts back to DHCP for both the wired and wireless connections after they disconnect unless you 'uncheck' the 'system setting' box)

Hope that helps! :)

---

### Post by BoomShaka on 2009-01-12
I've setup the port forwarding on my router to my ubuntu machine.
I'm also running firestarter and have setup the port forwarding, however I still get a Strict NAT type when I test the connection on the xbox.

Are there any debugging/troubleshooting tips anyone knows that could perhaps help me pinpoint the error?

I'm almost certain my router setup is correct, as I am able to SSH into my ubuntu remotely so I assume the other port forwards I setup should work fine too. My suspicion is that it is something I haven't done correctly in firestarter...

Any help anyone?

*begs*

---

### Post by Simply Stupid on 2009-01-12
i know this is random but please just click on the link thanks!

[http://www.brotherlyrevenge.com/index.php?c=viral&m=index&id=6c0d5e55d75ec5244fb990d19dcb77c1](http://www.brotherlyrevenge.com/index.php?c=viral&m=index&id=6c0d5e55d75ec5244fb990d19dcb77c1)

---

### Post by pmcchapman on 2009-01-14
> **BoomShaka said:**
> I've setup the port forwarding on my router to my ubuntu machine.
I'm also running firestarter and have setup the port forwarding, however I still get a Strict NAT type when I test the connection on the xbox.

Are there any debugging/troubleshooting tips anyone knows that could perhaps help me pinpoint the error?

I'm almost certain my router setup is correct, as I am able to SSH into my ubuntu remotely so I assume the other port forwards I setup should work fine too. My suspicion is that it is something I haven't done correctly in firestarter...

Any help anyone?

*begs*

Can you post your set up (IP addresses of router, pc, xbox) and a screen shot of your firestarter inbound traffic policy.

---

### Post by BoomShaka on 2009-01-14
Hey pmcchapman, I suppose that would be a good idea ;)
Firestarter screenshot attached

Xbox Network Setup
IP: 192.168.0.2
Subnet: 255.255.255.0
Gateway: 192.168.0.1
dns1: 192.168.1.254 - my router (some resources told me to leave dns blank, others to use my router, etc, not sure which is correct)
dns2: 208.67.220.220 - opendns (the dns I use in ubuntu)

My ubuntu machine's IP details are as follows:
eth0: 192.168.0.1 (wired to xbox)
wlan0: 192.168.1.66 (wireless to router to internet)

anything else that could be helpful?

---

### Post by pmcchapman on 2009-01-15
@BoomShaka

I think the reason the xbox is still reporting a strict NAT is that you have got the DNS look up wrong in the xbox.

Instead of your router's IP address, instead put in the DNS server(s) used by your ISP.

You should be able to find this either by opening the resolv.conf file in a text editor of your choice by typing the following command into the terminal, e.g.:

gedit /etc/resolv.conf

or

kate /etc/resolv.conf

etc.

Or, check your router's configuration when it is connected to the internet. Your router should detect your ISP's dns servers. Both of these should report the same thing.

If they are not the same thing, it could be because you appear to have manually set openDNS in the operating system. If using the DNS server of your ISP in the xbox configuration does not work, try setting the openDNS address for both look-up 1 and 2 on the xbox.

---

### Post by BoomShaka on 2009-01-16
@pmcchapman
I have setup the DNS for my ubuntu machine independantly of the DNS my router detects. I also recall using both dns1+2 as the OpenDNS IPs (edit: on the xbox of course) and that didn't work either, although I will try it again tonight when I get home.

Thanks

---

### Post by BoomShaka on 2009-01-16
Yep, as I expected setting both DNS entries to point to OpenDNS did not solve the strict NAT issue :/

nameserver 208.67.222.222
nameserver 208.67.220.220

Am I correct in my understanding that:
The router forwards the ports to my ubuntu machine, which then through firestarter forwards them on to the xbox?

---

### Post by pmcchapman on 2009-01-17
@BoomShaka

You are correct.

I'm afraid I have pretty much run out of suggestions...

I can only think of three more possible things to try:

1.) Ensure uPnP (universal plug and play) is switched on on your router.

1.) Temporarily adjust your router's configuration to put your wireless card's IP address in the DMZ (i.e. no protection from the router's firewall). If doing this solves the strict problem, then that would definitely suggest that the issue is the port forwarding settings on the router, so have another look at the manual port forwarding rules on your router.

2.) If the above does not immediately solve the problem, whilst leaving your PC in the DMZ temporarily try setting the DNS on the xbox and ubuntu to your openDNS. If that does not work, try setting them both to the DNS servers your ISP uses / provides.

If none of the above works, then I think I am out of ideas!

NB: Don't forget to revert back out of the DMZ on the router when you have finished, and revert if needs be to your original DNS settings.

---

### Post by BoomShaka on 2009-01-18
Thanks pmcchapman.
I've tried both those suggestions, but neither worked :/
I disabled my routers firewall completely (couldn't find a DMZ-like configuration) and that didn't help, as well as using the o2 broadband DNS entries.

I think I'll pop down to Game today and fork out the cash for a wireless adaptor. I connected via network cable to my router temporarily and it worked perfectly.

If anyone else has any suggestions I'll still try them, maybe I can return the adaptor to game if I get it working somehow.

Thanks again for the help pmcchapman

---

### Post by toasty mofo on 2009-02-21
> **Xecuter said:**
> I don't wanna install firestarter, how do i do it with iptables?

could anyone give information for this?

---

### Post by Firestem4 on 2009-02-21
is it at all possible to internet share a Linux with the XBOX?

---

### Post by mclaren on 2009-03-08
Okies..

So this is my first official post on here. I would first like to thank all the people who make the Ubuntu world what it is! AWESOME. Thanks guys! I have been surfing websites for hours now and have finally got my Xbox to connect to Xbox Live through Ubuntu without ANY NAT issue. OPEN NAT! I have been doing this on OS X and Vista and here is the Ubuntu way.

Step1:

Note down your router ip. The router your PC connects to get onto the internet. Mine is 192.168.1.1

Now your wireless cards (wlan0) ip. Mine is 192.168.1.100

On my router I have set ip 192.168.1.100 onto the DMZ. Check your router documentation on how to do this (alternately just use google!). If you dont want to do this you have to open up the following ports:
   
    * TCP 80
    * UDP 88
    * UDP 3074
    * TCP 3074
    * UDP 53
    * TCP 53

Step 2:

Set your Ethernet (eth0) card to set itself an ip: 192.168.0.1

To do this.

System > Preferences > Network Configuration > Edit
Then go to ipv4 Settings and select Manual from the drop down list.

Under Address. Click Add.
Address: 192.168.0.1
Netmask: 255.255.255.0
Gateway: 0.0.0.0

Leave DNS Server blank.


Step 3:

We now need a program called Firestarter.

Open up Terminal and type: sudo apt-get install firestarter

Now start Firestarter:

System > Administration > Firestarter

The Wizard should start up. If you already have firestarter then start the wizard.

Select your wireless internet device (wlan0).

On the first page uncheck 1) start the firewall on dial out & 2) IP address is assigned via DHCP. Again. UNCHECK both.

On the second page

CHECK 'enable internet sharing'

Local Area Network Device "Ethernet Device (eth0)"

Click Forward and Start Now.

Now go to policies:

Click on the area below "Allow Connections from Host"

Click on Add rule and enter ip: 192.168.0.2 

Now click on the area below forwarding service:

Click on Add rules and add 4 rules for the following ports:

80
88
3074
53

Now, we are done with Ubuntu


Step 4:

Goto your system settings and then network settings and enter the following:

Ip: 192.168.0.2
Subnet: 255.255.255.0
Gateway: 192.168.0.1

Primary DNS: 192.168.1.1
Secondary DNS: 192.168.0.1

AND YOUR DONE. Check Xbox Live Connection and cross your fingers. Mine went all through!

---

### Post by anachronist on 2009-07-18
I was finally able to get rid of the "Moderate NAT" problem. After installing Firestarter and setting the port forwarding, I discovered that it's the Xbox 360's UPnP that's getting blocked still. So, I installed linux-igd:

apt-get install linux-igd

Then, I ran this command:

upnpd wlan0 eth0

My laptop's running wireless to the Internet, while connected via ethernet to the Xbox. Network test in the Xbox works fine now, no errors about NAT.

---

### Post by notoriousmic24 on 2009-07-26
> **anachronist said:**
> I was finally able to get rid of the "Moderate NAT" problem. After installing Firestarter and setting the port forwarding, I discovered that it's the Xbox 360's UPnP that's getting blocked still. So, I installed linux-igd:

apt-get install linux-igd

Then, I ran this command:

upnpd wlan0 eth0

My laptop's running wireless to the Internet, while connected via ethernet to the Xbox. Network test in the Xbox works fine now, no errors about NAT.


When I try this, I get this:

user: socket creating failed: Operation not permitted
Invalid internal interface name 'eth0'

Any help?

---

### Post by fuzzman54 on 2009-08-16
I get the same error.

---

### Post by darkbillie on 2009-09-09
weirdest thing with me is if i open the orginal ports for the xbox it says moderated or strict but when i open them all (1 to 6500) its open...but then my pc gets exploited by the open ports.....so how do i solve this one

---

### Post by ~Niebr~ on 2009-10-07
it would be very tedious, but you could close one port at a time, testing each time, then youll know which one is which, it would take literally forever, but it would be nice to know! :D

---

### Post by lhall on 2009-11-10
Just an update for karmic(9.10). I gave my ethernet port an ip address, entered the ports for forwarding just as [BoomShaka]("http://ubuntuforums.org/member.php?u=323163") did in firestarter and my NAT issues are gone.

---

### Post by tekron on 2009-11-29
What a community-- thank you all from a desperate Xbox gamer!! :popcorn::KS:)

---

### Post by monocorn on 2010-01-08
> **notoriousmic24 said:**
> When I try this, I get this:

user: socket creating failed: Operation not permitted
Invalid internal interface name 'eth0'

Any help?

Have you run this as root?

Anyway for me it still is not working...

---

### Post by icroak on 2010-02-18
> **anachronist said:**
> I was finally able to get rid of the "Moderate NAT" problem. After installing Firestarter and setting the port forwarding, I discovered that it's the Xbox 360's UPnP that's getting blocked still. So, I installed linux-igd:

apt-get install linux-igd

Then, I ran this command:

upnpd wlan0 eth0

My laptop's running wireless to the Internet, while connected via ethernet to the Xbox. Network test in the Xbox works fine now, no errors about NAT.

Perfect. This did it for me. I didn't have to install firestarter. I just set eth0 to "Shared to other computers", ran the above command (as sudo) while the xbox is on and connected, and my connection is no longer moderate.

---

### Post by nathanhaynes on 2010-02-27
I know this is an old thread- but I was having some of the same issues, except my NAT type was strict.
I would just like to point out what I was doing wrong so that it might help others...
I was focused on the settings and port forwarding of my router- but totally forgot to check the actual settings of my modem! I even set my 360 in the dmz to no avail. 
It turned out that all I had to do was make sure that UPnP was enabled on the router AND modem, set up the port forwarding on my modem (not sure if this was even necessary, my isp told me that all my ports are open by default- check with your isp if you still have problems), and make sure that there were no conflicting settings between the router and modem.
I downloaded the UPnP universal control point program from Ubuntu's software center, which is what I used to find the IP address of my router. I typed that into my browser address bar which brought me to the settings of my router, where I modified setting as needed. Listed under "Default gateway" is where I found the IP to my modem. From there I typed in the IP of my modem and changed the settings according to my needs. I also followed the steps (except using firestarter) in this thread.
Viola! Works like a champ now.
Thanks for starting the thread- it was more help than any other source I found on the topic.

If you still end up with a strict or moderate NAT value- you might need to adjust the settings of your router/modem's firewall(s). In my case both my router and modem have individual firewalls with a low security setting.

---

### Post by FITH22 on 2010-03-08
Okay, get this if anyone can...lol  3 Xbox360's at one house, two say open and one said strict.  One connecting ethernet/wireless through mini mac(strict), one microsoft xbox360 wireless adapter(open), and the 3rd through a laptop ethernet/wireless(open).  The strict xbox would stay strict even when moved to the laptop and wireless adapter while the other two would stay open.  Wouldn't this tell you that is something to do with the particular xbox negating all the other networking config's.  Yes I've done DMZ, port fwding, still no joy.  Can you update firmware for the xbox?

---

### Post by bdufflebag on 2010-07-10
Wat do? Greyed out boxes down thar.

---

### Post by Caram3l B3ar on 2010-08-23
> **icroak said:**
> Perfect. This did it for me. I didn't have to install firestarter. I just set eth0 to "Shared to other computers", ran the above command (as sudo) while the xbox is on and connected, and my connection is no longer moderate.
Thank you icroak! Following anachronist original post and your tip to add "sudo" before the command line helped me to finally get rid rid of my annoying Moderate NAT problem. ****

---

### Post by dark racer on 2010-11-19
hey uhhm 
whith me its different 

i setup my eth0 to ipv4 tot share whith others but it also has ipv6 settings i put that on ignore and forwarded all the ports on firestarter 

i am using wirless to connect to linksys our wireless router and then use a ethernet kabel between my laptop and my xbox i setup the eth0 as described above im just renting a room here so i dont have acces to the router my resolv.conf says
domain tilbu1.nb.home.nl
search tilbu1.nb.home.nl
nameserver 192.168.1.1
nameserver 212.54.40.25
nameserver 212.54.35.25

my auto eth0 is
ip: 10.42.43.1
broadcastadres 10.42.43.255
subnetmask  255.255.255.0

auto linksys is
ip 192.168.1.102
broadcastadres 192.168.1.255
subnetmask  255.255.255.0
standerdroute  192.168.1.1
primary dns  192.168.1.1
secondary dns 212.54.40.25

xbox is setup like this

ip 192.168.1.2
subnetmask 255.255.255.0
gateway 192.168.1.1
primaty dns 212.54.40.25
secondairy 212.54.35.25


and it cant even connect to network
then i type in 
ifconfig eth0 up
ifconfig eth0 192.168.1.1
cat /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o ath0 -s 192.168.1.0/24 -j MASQUERADE

in terminal as root
and it can connect to network but not to internet and at this time my laptop cannot connect to internet aswel msn shuts down internet sites cant load end so on 

does anyone have a sugestion on how to fix this 
i do have to say i am a pretty new user to ubuntu
i got version 10.10 btw

ubuntu 10.10 (maverick)
kernel linux 2.6.35-23-generic
GNOME 2.32.0

thanks in advance

---

### Post by stevolime on 2010-11-20
just a tidbit here guys. sometimes the DHCP server will glitch up and make your open status go to moderate or strict. With this, the easy fix is to reboot or reset the network, meaning unplug the router, modem, etc. then plug them back in after about 10 seconds to let it reset, you don't lose your settings either.

another thing you can do is to turn off the dhcp server and use static ip address settings. doing this along with port forwarding will let you always have open nat. this is what i personally do and I have never had another problem with my NAT settings.

---

### Post by charliedontserf on 2011-02-26
> **anachronist said:**
> I was finally able to get rid of the "Moderate NAT" problem. After installing Firestarter and setting the port forwarding, I discovered that it's the Xbox 360's UPnP that's getting blocked still. So, I installed linux-igd:

apt-get install linux-igd

Then, I ran this command:

upnpd wlan0 eth0

My laptop's running wireless... 


I know this is an old thread but it was quite a merry search to find this little gem.


I found that this worked but in my scenario I had to link ppp0 to eth0. I got some odd error messages but it did the trick.

The problem is that the change doesn't persist through reboot. Anyone know how to make it permanent?

---

### Post by someitalian123 on 2012-06-06
> **charliedontserf said:**
> I know this is an old thread but it was quite a merry search to find this little gem.


I found that this worked but in my scenario I had to link ppp0 to eth0. I got some odd error messages but it did the trick.

The problem is that the change doesn't persist through reboot. Anyone know how to make it permanent?

I've been having the same issue, yet no one seems to respond to my threads. I even submitted this.

[http://brainstorm.ubuntu.com/idea/29809/](http://brainstorm.ubuntu.com/idea/29809/)

---

### Post by sffvba[e0rt on 2012-06-06
> **someitalian123 said:**
> I've been having the same issue, yet no one seems to respond to my threads. I even submitted this.

[http://brainstorm.ubuntu.com/idea/29809/](http://brainstorm.ubuntu.com/idea/29809/)

If the solutions in this thread didn't help I would suggest starting a new one and hopefully someone can assist.

*Old thread **closed**.*


404

---

