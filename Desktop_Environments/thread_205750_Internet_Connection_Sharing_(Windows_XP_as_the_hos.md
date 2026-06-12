---
title: "Internet Connection Sharing (Windows XP as the host, Ubuntu as the client)"
date: 2006-06-28
forum: Desktop Environments
---

### Post by seeknowsage on 2006-06-28
I am a complete newbie to LINUX/Ubuntu and I need some aid in getting a network I've setup up and running so both machines can connect to the net. As it is, I've followed the HOW-TO found at [http://ubuntuforums.org/showthread.php?t=72076](http://ubuntuforums.org/showthread.php?t=72076). My setup is almost exactly the same: I have a cable modem connected to an onboard nic on my windows machine, which is in turn connected to my ubuntu machine through a second onboard nic. I am able to ping either machine in my network from one another just fine. My windows machine can connect to the net just fine. However, I can't connect to anything on the Ubuntu side. Any and all help would be greatly appreciated (though I ask you kindly to not suggest reversing it so the Ubuntu machine is the gateway; remember, I'm still trying to get the hang of new razz-a-matazz. ;)

---

### Post by Shadowline on 2006-06-28
I know you might have a issue with this (due to money) but a router would fix this problem for you really quickly.
As to the cause of this.... ya got me...

---

### Post by seeknowsage on 2006-06-29
Thank you for your reply. Unfortunately, I do not have access to a router (I only have some dinky netgear hub as it is, heh), and I don't think I'd be able to get one in the near future. )=

---

### Post by seeknowsage on 2006-06-29
I somehow managed to get it working last night, but for the life of me I don't recall how (and I was moronic enough not to record the url of the steps I believe I followed). However, after messing around with things I didn't quiet grasp (again, my own ignorance for the win!), I decided to reinstall ubuntu 6.06 from the cd. (Note that no updates or anything else have not been obtain as of yet. The machine is running what's available from the install disc only.) I followed the guide listed in the first post for setting up my two machines to connect to the net. However, I'm back to square one again: My client ubuntu machine can ping my Windows XP host machine/nic and even my cable modem. However, it can't connect to the net at all. On the other hand, my Windows XP system can. Any and all advice would be greatly appreciated. Thank you.

---

### Post by seeknowsage on 2006-06-29
Further update: When I setup ICS on my WinXP machine and assign the sharing nic an ip of 192.168.0.1, and when I setup the nic on the client Ubuntu system with an ip of 192.168.0.2 and a gateway of 192.168.0.1, I'm able to ping the host nic, 127.0.0.1/cable modem, and the ip assigned by my isp. Moreover, it appears as though I can ping ip's for various websites (yahoo, digg, etc.). However, I am only able to do so one time; if I ping another ip or close the networking tools window in Ubuntu, I can't ping the same ip. Nevertheless, I am able to still ping other ip's.

Is this a DNS issue? (I know for a fact that I didn't alter this when it was running last night.) Do I have to do some special configuration to my nic I have yet to see? (As it is, the various pages I've read covering this suggest I only need to assign an ip and gateway to the shared system/nic.)

---

### Post by StylusPilot on 2006-06-29
[COLOR=Blue]I used to have a sort of similar setup, but have recently moved house and its all changed, however what I used to have was this.

I had an ADSL Modem/Wireless Access Point connected via Wireless to my Windows XP PC

Then via Ethernet a CROSSOVER cable to my Ubuntu Machine. (didn't have a wireless card on the ubuntu machine)

My ubuntu machine was simply set to DHCP and no other changes made to it. (As the Windows machine will be a mini DHCP Server)

Then on the Windows XP Machine I went into the Network Setup Wizard, and choose "This computer connects directly to the internet and other computers connect through this computer" and told it the wireless was my internet connection.

Once the wizard was finished you will see that XP makes you have the IP Address of 192.168.0.1 on the shared NIC, which is the IP that ICS will use. 

Then I made sure that the settings were still correct on the Wireless Card.

[/COLOR][COLOR=Blue]In the TCP/IP Settings for the Wireless Card I had it all on DHCP as my ADSL Modem was also router. The XP machine could then access the Internet as per normal via Wireless.

Not sure if that would be the same for you as cable is different right? Never used cable before so I dont know.
[/COLOR] [COLOR=Blue]
I then right clicked on the ethernet connection and went to properties and made sure that "Allow other users to connect through this computers connection" was selected.

The Ubuntu machine was then being given an IP Address of 192.168.0.66 which I checked with the good old ifconfig. And the default gateway was automatically 192.168.0.1 (XP Machine)

And it could browse the internet fine, sort of like a mini NAT through the XP Machine.

Hope this was a help is some way.

EDIT: There is also somewhere where you set what IP Adresses ICS gives out, I can't remember where though. You could always try setting that to only 1 address, or try and turn the DHCP part off and manually put an IP on the Ubuntu Machine, but DHCP should work.

EDIT 2: Make sure the Windows Firewall has the exception for ICS in it. and make sure there is no Ubuntu Firewall or whatever.
[/COLOR]

---

### Post by seeknowsage on 2006-06-29
Thank you very much for your help. I followed your instructions to the letter, save for a couple of places. Since I'm running cable, I did leave the default TCP/IP settings it uses to automatically obtain an ip and dns server. Also, I while I don't know if this is actually an issue or not, but my "Local Area Connection 2", which is what windows recognizes as my ethernet connection to my ubuntu machine, does not have the option for internet connection sharing. This option is only on "Local Area Connection", which is my cable connection. Anyways, after following the steps you outlined, I am still unable to connect. I don't run the Windows firewall, but I do run zone alarm pro. I am unsure if this would detect the connection or not. (Last night, when it was working, I don't recall receiving any errors/warning from ZA.) Also, I don't believe I have a firewall installed in Ubuntu yet, but I am not entirely sure on how to check that.

---

### Post by StylusPilot on 2006-06-30
Try turning of Zone Alarm for a test.

So on the cable connection do you have "Allow other users to connect through this connection" enabled?

Is DHCP enabled on the Ubuntu machine?

Is the Ubuntu machine machine receiving a DHCP address from the XP machine?

---

### Post by seeknowsage on 2006-06-30
I've been playing with it for the past 20 minutes, and you are right. It is definitely zone alarm pro.

When ZA is disabled, I can connect. However, I have defined the ip on the ubuntu nic. I haven't changed it to DHCP yet, but I can and probably will later once I get the ZA quirk ironed out.

As it stands, I am trying to determine what the local address is that ZA prompts me for for the ICS. (I thought it would be 192.168.0.1, but I don't think this is it.)

Anyways, thank you very much for your help and I apologize for wasting everyone's time on this. (Apparently, I had ZA disabled last night, which is unusual b/c I *never* do that.) Again, thank you. (=

---

### Post by StylusPilot on 2006-06-30
Zone Alarm can be weird sometimes, I'm glad you got it working.

Best of Luck.

---

### Post by blkdragon on 2006-09-21
WHOA!

awesome, man. it totally works!!

thanks a lot.

---

