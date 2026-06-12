---
title: "Anyone else..........."
date: 2009-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tearaft on 2009-09-11
.......experience this?

My new Dell Inspiron 15n (running Ubuntu 8.10) came yesterday. I was surprised how nice it was, IMHO almost in Apple territory when it comes to looks. It started and runs fine BUT I can't get it on the net. I'm using a Motorola SBV 5220 Surdboard modem. I was just wondering if anyone else has had this problem. I don't think that my modem is rare (everyone in my area who has broadband has one) so I figured it would work, but so far nothing. So, has anuone else had this problem and if so, were you able to correct it? I don't want to send it back (shipping costs and restocking fees) but if I can't get it online I'll be forced too. 

PAX

Tom

---

### Post by gbrainin on 2009-09-11
I don't know if I can help, but I do know it would help to have some additional information.  For example:

[LIST=1]
[*]Have you confirmed that you can connect with a different computer using this modem?  (Dumb question maybe, but worth asking.)
[*]Are you connecting via wireless or ethernet?
[*]Is the network manager applet reporting any errors, or is it connecting to the network card OK?
[/LIST]

There are probably other questions, but that's a start toward trying to diagnose your problem.

---

### Post by Dennis N on 2009-09-11
Are you using a router, or are you connecting directly to that modem with ethernet or USB cable?

---

### Post by hoppy3 on 2009-09-12
I too got a new dell mini with ubuntu 3 days ago and it would not connect to the internet when I switched the modem cable from my desktop to the mini. 
Discovered I had to unplug the modem a/c plug for 30 seconds, and plug back in to connect to the internet. 
Also, I have to do this again when connecting the cable back into my desktop.
Good Luck.

---

### Post by Tearaft on 2009-09-12
Hi guys,

Sorry that I didn't provide more info.

-Yes, I am using the same modem right now on my iMac which is dual booting with Ubuntu 6.06 which has no problems connecting.
-I am connecting via ethernet.
-Not sure what you mean about the network manager. What type of errors should I look for?
-I am connecting directly to the modem.
-I will give you suggestion a try Hoppy. 

Thanks for all of your help.


PAX

Tom

---

### Post by ikt on 2009-09-12
Check the system log when you plug the ethernet cable in, see if there's any errors there.

It is a bit strange that it's not picking it up. Possibly faulty port?

---

### Post by Tearaft on 2009-09-12
Hi again,

I tried your suggestion Hoppy, and it didn't work. Thanks for trying.

Perhaps this can be of some help.

In Network tools from the Devices tab I have three options.

The first/default is loopback interface (lo).... In internet info it's not available for all categories, under interface statistics it's all zeros.

The next option is Ethernet Interface (eth1) with that it says that I am receiving bytes between 200 kib and 1 mib's. plus I am getting packets(does this mean I am connected?) but interface info is not available.

What do you think?

The third option is Ethernet Interface (eth1) and again all zero's.

Thanks for all of your help. I really appreciate it. The whole community aspect is one of the reasons I came back to Linux. It fits in well with my views on life (I am in training to be a Franciscan Friar)

Pax

Tom

---

### Post by gbrainin on 2009-09-12
I'm not quite sure what you're referring to when you say "Network tools from the Devices tab."  Devices tab on what program?

However: Unless you mistyped something, it seems like you have two sets of settings for the same ethernet port (eth1).  That could be causing the conflict that prevents the system from properly connecting.

Also, normally on a Linux system the first ethernet port is eth0, so it's odd that didn't show up.

I'd be tempted to try deleting the second instance of eth1, but since I don't know what program you're using to access the information, I am a little leery of suggesting that you make changes that you might not know how to undo if they don't work.

EDIT: Never mind, I found the program you're talking about (System->Administration->Network Tools).  If it's reporting packets in and out without errors, that indicates there is some traffic.

Does it show the interface having an IP address?  If not, the problem may be in getting a DHCP address from the modem.

---

### Post by Tearaft on 2009-09-12
Loopback interface which is default (at least it shows up first is receiving bytes and packets now. No reception errors, IP address is 127.0..0.1, State is active.

(etho) is receiving more packets and bytes no errors but no Ip and all of the interface info says not available.

(eth1) all stats say 0 no IP, Interface info not available.

---

### Post by uconvert on 2009-09-12
I have a 1525, and it has a little switch on the right side that disables the wireless to accomodate what I assume would be a Verizon or Sprint mobile wireless thingy. I went through two cycles of trying everything, even using my intermittent ethernet cable which I threaten to replace every payday, but never do. 

If you have a switch on the left side toward the front try toggling it to see it that works.

---

### Post by Tearaft on 2009-09-12
Thanks Unconvert but I wasn't able to find any switch on mine.

Do I have to put an IP address in somewhere?

DCHP?

It seems like I maybe so close but still nothing.

---

### Post by Dennis N on 2009-09-13
A couple of ideas to consider: If you haven't done so, I would take the laptop out where I could test a wireless connection, such as a public library with internet access. Also, using a router might make things work better and give you a wireless option. I have a Motorola modem (not the same model as yours) which does not have a built in firewall, so adding the router provides that too. Settings, status, and network addresses can be read easily from the router's control page (accessible from Firefox) to see what is going on.

---

### Post by gbrainin on 2009-09-13
> **Tearaft said:**
> Do I have to put an IP address in somewhere?

DCHP?

It seems like I maybe so close but still nothing.

It appears that your computer's ethernet port (eth0) is talking to the modem's; that is the most likely explanation for the report that there is traffic on the port.  That's a good thing, since it eliminates several possible sources of this problem.

However, in order to have any meaningful internet connection, you have to have an IP address assigned to the port.  Otherwise, all the communication between the computer and the modem pretty much boils down to "What's your IP address?"  "I dunno."  Not very useful.

There are two ways that an IP address can get assigned to a port: Manually, or through DHCP ("Dynamic Host Configuration Protocol"--not that that really helps you understand what it means).  DHCP is pretty much standard these days, which is why I've been assuming that both your modem and your computer are set up that way.  The way that works is that one device (in this case, the modem) is set up to assign IP addresses to any devices that ask for one.

So, the question is, why does your other computer get an IP address (it must have one, if it's getting internet connection) but the new computer doesn't?  Most likely, the settings of at least one of the machines (the new computer, the old computer, or the modem) is not what the other ones are expecting.

So, I would suggest you look at the settings of the computer that works, for a start.  Try to find out a) what IP address the computer gets assigned, and b) whether the computer is set to get that IP address via DHCP, or if it is set manually.  Then try to reproduce those settings on the new computer.

BTW, I agree with the suggestion, above, that a router is a good idea.  Even if you've only got one computer at a time connected, it does provide some valuable firewall protection.  You can pick one up for well under $100, even less if you get one without wireless built in.  But let's see if we can't get your computer working before we send you out to buy new hardware.

---

### Post by Tearaft on 2009-09-13
Thanks gbrainin and everyone,

Sorry, about the typos.

I have my IP address from the computer that I am using to post (I made sure to get it the night before my Dell came in anticipation that I might need it). It is using the same Motorola modem. It's an old iMac G4 800mhz circa 2001-02. Now, if it was put in manually or via DHCP, I don't know.  I did not put it in the cable guy did when he hooked me up last year. He seemed to have a bit of trouble doing it but I think that had to do with him being  unfamiliar with Apple computers. 

I've tried to enter it into the laptop but I'm not sure how too do it. When I used Linux in the past (many moons ago back in the days of RH 7-8 and Mandrake) I was using dial up and was able to set everything up myself. But now I am very far out of the loop when it comes to Linux and clueless about high speed modems.

I didn't know that routers were so cheap! I know nothing about them since my network at home simply consisred of two iMacs connected via a Cat 5 crossover cable . So maybe I will purchase one in the future (perhaps even the near future) but for now I would just like to get the internet connection problem fixed before I spend anymore cash. But thanks for the advice. I would have no need for wireless so I would be able to get the one of the cheaper ones!

Pax 

Tom

---

### Post by Tearaft on 2009-09-14
I logged into my root account on my Mac and checked system preferences. It says that I am using DHCP with IPv4. It also gave addresses for both "subnet mask" and "router".

Pax 

Tom

---

### Post by gbrainin on 2009-09-14
OK, so far so good.  Now, on the new computer let's check to make sure it's trying to use DHCP also.  Go to System->Preferences->Network Configuration.  Select the Wired tab, then select your primary ethernet connection (eth0).  Press the edit button.  In the new window that comes up, select the IPv4 Settings tab.  Under Method, does it say "Automatic (DHCP)"?

---

### Post by Tearaft on 2009-09-14
Yes, it says Automatic (DHCP)

---

### Post by gbrainin on 2009-09-14
> **Tearaft said:**
> Yes, it says Automatic (DHCP)

Hmm.  Well, so much for the easy answer.  Let's go back to why there is an eth1 listed on your system.  Do you have two physical ethernet ports?

Try taking a look at the network configuration for each, and write down the MAC address (System->Preferences->Network Configuration, select an adapter and hit Edit).  If the MAC address for eth0 and eth1 are the same, try deleting eth1 and see if that helps (you may need to reboot after doing so before you notice a difference).

---

### Post by Tearaft on 2009-09-14
I will do it now.

---

### Post by Rhubarb on 2009-09-14
Another suggestion that may be of help for you:-

Try using the USB connection to your surfboard modem.
I know from experience that I once came across this problem, where the USB connection worked in ubuntu, but the ethernet connection did not work.

I can't explain why this was the case, but it did work for me before.
Usually I prefer to connect via ethernet, but sometimes this doesn't work (easily).

---

### Post by Tearaft on 2009-09-14
I only have one physical port.

I have only one entry under network connections  (auto etho) so I didn't want to delete it.

my MAC address is 00:25:64:57:68:26 (don'y know if that means much)


Under IPv4 tab  there is no address.

Under Devices- Network Tools eto is receiving packets, eth1 is not


sorry for the delay in a responseh

---

### Post by Dennis N on 2009-09-14
A couple of simple things you might check:

I may have missed something, but did you actually check for an IP address assigned to the new laptop? A few posts up, you said you were wondering if you should enter it someplace. A simple way to find the assigned address is just open the terminal and type:```


ifconfig
```

This command reports all active network interfaces.

Look at the second line in the eth0 section. If it begins 'inet addr:' followed by an IP address, you should be good.

Typing 'exit' with close the terminal window.

Secondly, check the networking applet on the top gnome panel (with the two little computers, or the 4 bars). Double click on it and be sure the desired networking type (wired or wireless) you want is actually enabled. It could have been turned off somehow.

---

### Post by Tearaft on 2009-09-14
I ran ifconfig
 I got results from both etho and eth1 in that order.

the second line of each reads inet6 addr: fe80 : : 225 : : 64ff : fe57 : 6826/64 (etho)

and inet6 addr: fe80: : 222 : 5fff : fef2 : a66f/64 (eth10

As for the networking applet the only option it gives is autoetho, and yes I double click it each time and the little green graphics swirl and then it give a message of could not connect or no connection.

Thanks

Tom

---

### Post by Tearaft on 2009-09-14
Looking at the addresses are they IP addresses?

I'm guessing that the 80 is reffering to the port but why all of the letters? 


Is the solution to delete etho and replace it with eth1? if so how?

---

### Post by Dennis N on 2009-09-14
Ok, there is something different there from what I get (my output below). You apparently aren't receiving an IPV4 address (see line 2 below) from the DHCP server, only IPV6 (line 3). My output shows both, which might be normal, as both my computers here show both types. On the other hand, maybe only one is required? I would check with the ISP tech support and ask about this. BTW, Do they supply the modem?

```
dmn@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a1:c9:90  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fea1:c990/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4839461 (4.6 MB)  TX bytes:908209 (886.9 KB)
          Memory:fdfc0000-fdfe0000
```

---

### Post by Tearaft on 2009-09-14
Yes, the modem came for the cable co.

---

### Post by Tearaft on 2009-09-14
This may not be good news. I was hoping the problem wasa software problem with my computer, something I could control and not with the modem.

---

### Post by Tearaft on 2009-09-14
Rhubarb,

Sorry I missed your post. How would I go about connecting via USB to my modem?

---

### Post by Tearaft on 2009-09-14
Rhubarb,

Never mind. I checked the back of my modem and saw the USB port. I had no idea it was there. I found one old USB cord that I had but it didn't fit into the laptop. One question, would my connection be slowed much via USB? I don't want a connection that is that much slower, I lived with dial up for about 8 years and now that I have broadband I can't go back. I just can't


PAX

Tom

---

### Post by Dennis N on 2009-09-14
On USB connection to modem:

According to the Motorola user manual for my modem model, the USB connection only works with Windows computers. Yours probably has the same restriction.

---

### Post by Rhubarb on 2009-09-15
> **Tearaft said:**
> Rhubarb,

Never mind. I checked the back of my modem and saw the USB port. I had no idea it was there. I found one old USB cord that I had but it didn't fit into the laptop. One question, would my connection be slowed much via USB? I don't want a connection that is that much slower, I lived with dial up for about 8 years and now that I have broadband I can't go back. I just can't...
Your connection will not be slowed down when using USB, that is unless your broadband is faster than 8MBit or so - then there's a chance it'll be slower.

The USB cable that you'll need is a USB-A to USB-B cable, you can find them at any computer shop for a few dollars.


> **Dennis N said:**
> On USB connection to modem:

According to the Motorola user manual for my modem model, the USB connection only works with Windows computers. Yours probably has the same restriction.
This is more the case that Motorola only provides support for Windows computers, it by no means states whether it works or not with non-windows computers.
- From experience I've found that Ubuntu works very nicely with (atleast some) Motorola Cable modems via USB
You may need to turn the modem off for a minute before turning the unit on again when connecting via USB.

---

### Post by Tearaft on 2009-09-15
Huh, if this is the case than USB may be the answer to my problems. If I can get out tomorrow (I am disabled so getting around and out is day to day) I may go to Staples and pick one up.

PAX

Tom

---

### Post by Dennis N on 2009-09-15
Rhubarb,

If you've done it, it must be so. I only reported what the manual claims:

> Windows® 95, UNIX, Linux, or Macintosh computers must use the Ethernet connection.

Hope it all works out.

---

### Post by gbrainin on 2009-09-15
> **Tearaft said:**
> I only have one physical port.

I have only one entry under network connections  (auto etho) so I didn't want to delete it.

my MAC address is 00:25:64:57:68:26 (don'y know if that means much)


Under IPv4 tab  there is no address.

Under Devices- Network Tools eto is receiving packets, eth1 is not


sorry for the delay in a responseh

It is VERY strange that Network Tools reports two ports (eth0 and eth1) but Network Configuration only reports one.  Have you looked through the other tabs in Network Configuration (Wireless, DSL, etc.)?

I do NOT suggest deleting eth0.  My theory was that you somehow got two configurations (eth0 and eth1) for the same physical port, and that was somehow causing a problem.  If that were the case, then eth1 would be the "extra" one that needs deleting.

I also like the other ideas you've been presented.  Keep on trying things; one of them is bound to work.

Final thought: You can probably use the other computer to connect to the configuration screen for the modem.  If it's assigning an IPv6 address but no IPv4 address (which is what it appears to be doing), the problem may be the settings on the modem.  Unfortunately, you'll need someone familiar with that modem to guide you through the process, and that's not me.

---

### Post by Tearaft on 2009-09-15
Hi everyone,

I AM FINALLY ONLINE! All it took was a simple phone call to my ISP and within roughly ten minutes my problem was solved. All that needed to be done was to reset the modem from my Mac to the Linux laptop.That was it. I wasted five days and a lot of your time as well by not doing the most obvious thing. I apologize for wasting your time. My excuse for not calling my cable co. was that 
when I first got the laptop (last Thursday) I figured that if I would have called them they would have just scheduled me for an appointment perhaps in a week or so and then the Tech would have arrived and would have not known anything about Linux(the last one didn't know much about Apple). So it would have been a waste of time.I figured I would have the problem fixed before they could have  gotten here. I guess I should have had more faith in them. 

So, thanks again everyone. I maybe posting again sometime but if I do it may very well be under a different name because I am so embarrassed about this.

GOD BLESS 

PAX

Tom

---

### Post by gbrainin on 2009-09-16
Don't be embarrassed.  The solution to problems like this always seems obvious after you know what it is.

I'm glad your computer is working and online now!

---

### Post by Rhubarb on 2009-09-16
Owww, why didn't I think of that?
Don't be embarrased, atleast you found the solution, and we all learned from this so we shouldn't fall for such a problem in future.

Thanks for sharing the solution too! :)

---

