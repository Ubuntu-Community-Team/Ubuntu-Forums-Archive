---
title: "The Xbox 360, network bridge &amp; ubuntu = EASY!"
date: 2009-06-10
forum: Gaming &amp; Leisure
---

### Post by fleaaccela on 2009-06-10
Seriously. I can't believe how simple Ubuntu is to use. It's like having a magic man make it all work with no problems. Another shout out to the open-source community & Ubuntu developers for being the awesomest ************* on the planet!!!!!!!

I got a wireless USB card. Was using it as normal for an internet connection. Of course, I have an RJ-45 connector for my onboard ethernet connection. In Windows, I had my machine set up to provide an internet connection to this port using a network bridge created in the settings (is that the correct term - network bridge?).

Anyhow, I just decided to see if this setup would work in Ubuntu as well on a whim.

Edit connections
Wired > Auto eth0 > Edit
IPv4 Settings > Method : Shared to other computers
Apply

And oddly enough, somehow it worked. I know I had no internet connection going through it before because my Xbox wouldn't connect. Now it does. And all I did was do some basic guessing and it worked!

So thanks, guys! Every day I get more pumped up and pleased with how frikkin AWESOME Ubuntu is for the average end-user. It's by far the best blessing I've had as far as computer experiences in my entire lifetime. No wonder Windows users refer to the Linux community as "fan boys". I can see why, now. Why wouldn't you be one? :D

---

### Post by realgt on 2009-07-25
in case you're still not seeing this work, make sure to turn on your eth0 connection


sudo ifconfig eth0 up

---

### Post by s5demigh on 2009-11-10
Wow, this was going to be the one thing that kept me from making the switch (again). Thanks for this. I'll try it out asap!

---

### Post by ArrrghJ on 2009-12-26
I can only get on with a Moderate NAT...
Any suggestions?

---

### Post by VastOne on 2010-01-17
> **palluvinny said:**
> You are the man! Worked like a charm. woot finally am there

What exactly worked like a charm?

---

### Post by ELD on 2010-04-03
I know this is an old thread but please don't lock it for the updated reply from me.

I have just tested this under 9.10 and i thought it didn't work, but i turned my xbox on and off and then ubuntu popped up saying "auto eth0 connection establish" or whatever it says and it works perfectly, it wouldn't work at all under Windows7, that is a big big big one up for Ubuntu and Me :D

---

### Post by radgiegadgie on 2010-04-05
I spent ages reading up on how to create a bridge so I could connect my ps2 in the same way. When I eventually figured it out, I couldent belive it was so easy. Most guides on doing this seemed to run to pages of complex things that needed to be done, in order to achieve the bridge.

---

### Post by ELD on 2010-04-05
I know it's crazy all you need to do is edit it to make it shared and it works right away, ubuntu even pops up the notification to tell you it has connected as well, easy peasy!

---

### Post by marcelluspye on 2010-04-05
> **radgiegadgie said:**
> I spent ages reading up on how to create a bridge so I could connect my ps2 in the same way. When I eventually figured it out, I couldent belive it was so easy. Most guides on doing this seemed to run to pages of complex things that needed to be done, in order to achieve the bridge.

Even better, you can install linux onto your PS2 and dual-boot Ubuntu(I think, though many others also work) as well as the PS2 Native operating system.

---

### Post by ELD on 2010-04-05
Daul booting on the ps2 won't solve the problem of playing ps2 games across the net on it, that is the whole point of doing the bridging [marcelluspye]("http://ubuntuforums.org/member.php?u=863241").

---

### Post by ookami-no-kobushi on 2010-08-04
hello there, im kinda new to the forums on here, im also a relativly new Ubuntu User, and i must admit it has done wonders with my laptop, it was running windows vista on 1 GB of ram, any way im rambling, i have tried the suggested method, and needless to say it has worked, how ever i have ran into a little problem, as i have reset the factory defaults on my Xbox 360 to release my nat type from "strict" to "open" then when i tried to reconnect my 360 it now wone connect, for some reason ubuntu now wont allow the bridge, how can i correct this ?

---

### Post by ELD on 2010-08-05
Why does the message say when you try to use the bridge or if you can't even enable it anymore what does it say when you try to turn it on?

---

### Post by Lukios on 2010-08-31
Just thought I would throw this out there, but this also works for credit card machines, at least the one I am using which is a Hypercom T4220. I believe it will work for most other machines as well.

---

### Post by ELD on 2010-09-01
> **Lukios said:**
> Just thought I would throw this out there, but this also works for credit card machines, at least the one I am using which is a Hypercom T4220. I believe it will work for most other machines as well.

It will probably work for most things that require an internet connection that you wish to share :)

---

### Post by DenisQC on 2010-10-10
I was looking on Google for a way to do just that (replace laptop with desktop and XBOX for PS3 though). I tried it and then not only does it not work, but it also shut down the internet on the source computer... I need to revert back to Automatic (DHCP) and restart the connection to be able to have internet again!

Anyone have an idea what I am doing wrong?

EDIT : By reading the first post again, I realized it was from wireless to wired, while I was going for wired to wired. That means I have two eth connections. I set the sharing on eth1 and it worked!

---

### Post by Macbuntu-Windows-7-User on 2010-12-22
I did this theory, too on my computer on my Macbuntu (Ubuntu with Mac theme) 10.10 Hard Drive (13.5GB IDE HDD) and my computer currently has Windows 7 on my 1TB Hard Drive.  With Windows 7, you have to bridge the Wireless card and Ethernet card without any of them with Internet Connection Sharing enabled and takes forever to make a network bridge. On my Macbuntu hard drive, it took me forever to do a network bridge. I tried firestarter and bridge-utils and no dice, but when I read this thread, I finally got Internet connection for my Linksys WRT54G Router for my Xbox 360 via Ethernet and other devices via Wireless Access Point.  The problem is that you have to check the box that says "Connect Automatically" for the Auto eth0 connection and same for the wireless connection under System > Preferences > Network Connections > Wireless > Auto <SSID>* <SSID> is your Wireless Connection and under System > Preferences > Network Connections > Wired > Auto eth0*

*"Connect Automatically" must be selected for auto-connectivity.

To see if your connection is live, go to Menu > Accessories > Terminal and type in sudo ifconfig, and enter your password.  Then, scroll to eth0 and wlan0 to see if your devices have the IP addresses. If not, enable the connection by typing sudo ifconfig eth0 up and sudo ifconfig wlan0 up or just do the steps above to have a live Internet connection.  This works for me, and this should work for you.  If any of you guys have any problems, send me a Private Message and I'll help you.  And I'm new here.

I'm Benjamin Josef Wilson and I'm a proud Ubuntu and Windows user.
Have a great day, everyone and Merry Christmas and Happy New Year.

---

### Post by spriggsey on 2010-12-23
when i try to do this it cant even assign an ip to my xbox properely but if im not connected wirelessly on my computer for some reason my xbox can connect to my computer but when i reconnect to the internet.. boom my xbox loses its ip address n things and falls at the first hurdle... helpppp

---

### Post by Macbuntu-Windows-7-User on 2010-12-25
> **spriggsey said:**
> when i try to do this it cant even assign an ip to my xbox properely but if im not connected wirelessly on my computer for some reason my xbox can connect to my computer but when i reconnect to the internet.. boom my xbox loses its ip address n things and falls at the first hurdle... helpppp
Good day, and welcome to the Ubuntu Forums!

Go to the Network Connections Icon on the toolbar, right-click on the icon and select Edit Connections.  Go to Auto eth0 and verify the settings via IPv4 and make sure the "Shared to other computers" is selected and make sure that you have the "Connect Automatically" is selected, click Apply. For the Wireless Connection, click on the Wireless Tab, select "Auto <SSID>" and click Edit.  Make sure the "Connect Automatically" is selected and re-connect again. Otherwise, put a Static IP address in the Xbox 360 by putting 10.42.43.2 as an IP address, Netmask: 255.255.255.0, Default Gatway: 10.42.43.1, DNS1: 10.42.43.1, DNS2: 0.0.0.0

If you need to leave the connection running after a computer power cycle, aka Reset, make sure the "Connect Automatically" is selected in both the eth0 and wlan0 interfaces.

Then, go to Applications > Accessories > Terminal and type in the following: sudo ifconfig and type in your password to make sure your Linux machine has the following fields in the wlan0 and eth0: IP Address, Broadcast Address, and Subnet Mask

Broadcast Address: Depending on the subnet mask/ip prefix, the last binary octet is 255
11111111 = Broadcast Address Last Octet (2^7*1)+(2^6*1)+(2^5*1)+(2^4*1)+(2^3*1)+(2^2*1)+(2^1*1)+(2^0*1)

2^0=1
2^1=2
2^2=4
2^3=8
2^4=16
2^5=32
2^6=64
2^7=128

Example:
Network Address: 172.16.0.0/24
Broadcast Address: 172.16.0.255/24
Useable Hosts: 172.16.0.1/24-172.16.0.254/24

/24 - IP Prefix (255.255.255.0 - Subnet Mask)

---

### Post by Schuby007 on 2011-02-01
Do you need a crossover cable for the connection between the computer and the "device" (xbox)???

---

### Post by Schuby007 on 2011-02-01
Hi,

I have a desktop running 10.04 and I'm trying to use my laptop running 10.10 which is connected to my wireless router via wlan0 to provide internet to my desktop via eth0 to eth0 on the desktop.

I went into Network Connections on my laptop and did Wired->Auto eth0->Edit->IPv4 Settings and selected "Shared to other computers" under Method. And selected "Connect automatically", hit Apply and then did Wireless->Auto<SSID>->Edit-> and selected "Connect automatically", hit Apply. Rebooted. Tried hooking the computers up with a crossover cable and then a regular ethernet cable but the desktop wouldn't connect. When I plugged in the cable, the laptop would pop-up saying "Connected" and I would select Auto eth0 on the Desktop's Network Manager drop down and the wireless signal meter thing would flash for about 20 seconds and then it would say "Disconnected".

So I then decided to input the settings manually into the Auto eth0 on the Desktop.
I did Network Connections->Auto eth0->Edit->IPv4 Settings-> switched Method to "Manual" and input:
Address - 10.42.43.2
Netmask - 255.255.255.0
Gateway - 10.42.43.1
DNS - 10.42.43.1
and selected "Connect Automatically", hit Apply and then tried to connect. It connected! However, I went to my browser and I wasn't able to search the web. Firefox said "Server not found"

Can someone please help me get this working.
Thank you.

---

### Post by dannyboy79 on 2011-11-14
> **Schuby007 said:**
> Hi,

I have a desktop running 10.04 and I'm trying to use my laptop running 10.10 which is connected to my wireless router via wlan0 to provide internet to my desktop via eth0 to eth0 on the desktop.

I went into Network Connections on my laptop and did Wired->Auto eth0->Edit->IPv4 Settings and selected "Shared to other computers" under Method. And selected "Connect automatically", hit Apply and then did Wireless->Auto<SSID>->Edit-> and selected "Connect automatically", hit Apply. Rebooted. Tried hooking the computers up with a crossover cable and then a regular ethernet cable but the desktop wouldn't connect. When I plugged in the cable, the laptop would pop-up saying "Connected" and I would select Auto eth0 on the Desktop's Network Manager drop down and the wireless signal meter thing would flash for about 20 seconds and then it would say "Disconnected".

So I then decided to input the settings manually into the Auto eth0 on the Desktop.
I did Network Connections->Auto eth0->Edit->IPv4 Settings-> switched Method to "Manual" and input:
Address - 10.42.43.2
Netmask - 255.255.255.0
Gateway - 10.42.43.1
DNS - 10.42.43.1
and selected "Connect Automatically", hit Apply and then tried to connect. It connected! However, I went to my browser and I wasn't able to search the web. Firefox said "Server not found"

Can someone please help me get this working.
Thank you.
im currently having tons of issues getting my xbox 360 to work with Network Manager ICS as well and wanted to point something out I noticed for your setup

You connection to your router over wifi, edit the dns servers so they refer to opendns instead of using your router built in dns forwarder. it doesn't work very well on many routers. so it would 208.67.222.222 for your DNS. try that

---

