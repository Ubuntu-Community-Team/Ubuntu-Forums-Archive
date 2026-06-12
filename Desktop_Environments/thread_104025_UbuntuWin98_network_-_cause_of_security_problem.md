---
title: "Ubuntu/Win98 network - cause of security problem?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by stig on 2005-12-15
[EDIT: Solution added in last post]

Hi,
Since adding Ubuntu PCs to my Win98 DHCP network one of the Win98 PCs shows up as insecure on a Sygate port scan. I wonder whether this insecurity could be linked to the addition of Ubuntu? I am a beginner on Linux and would welcome some help.

I had three PCs networked on Win98 with a router (Thomson Speedtouch) using DHCP and linking them to the Internet. On a Sygate port scan they each always showed the router IP address (a number beginning with 80) and were reported as fully blocked and &#8220;stealthed&#8221;.

Recently I changed one of the PCs from Win98 to Ubuntu 5.10 and also added Ubuntu on a second hard disk in one of the other PCs. I used Nautilus-Share to set up file sharing and now have all the PCs linked together on the network.

But now when I do a Sygate scan the Ubuntu PC, the Ubuntu hard disk, and the Win98 hard disk all show the router IP and are fully blocked - but the Win98 PC is different. It shows an IP address beginning with 193, it appears to have three ports open, and all the other ports are described as closed rather than blocked. Every time I do the Sygate scan on this PC I get the same result - but, curiously, a scan by ShieldsUp shows the same PC as fully stealthed.

The Sygate results are shown below. Nothing in the network settings has been changed on the Win98 PC since adding the Ubuntu PCs and I don&#8217;t know how to account for the different Sygate result unless it is something to do with adding Ubuntu to the network. Connections to the internet and email work as normal on this PC. The router acts as a firewall and so I don&#8217;t understand how Sygate gets this result. The other Win98 PC on the network still shows the router IP address and performs as fully stealthed on Sygate. If anyone has encountered this before and can suggest reasons and solutions I would be very grateful!


Result from Sygate scan:
We have determined that your IP address is 193.195.0.101
This is the public IP address that is visible to the internet.
Note: this may not be your IP address if you are connecting through a router, proxy or firewall. 
Trying to find out your computer name... 
Unable to determine your computer name! 

Trying to find out what services you are running... 
Web Server Found = Server: NetCache appliance (NetApp/6.0.1) 
Telnet Open = #
FTP Server Open = 220 [there is a web URL here]. (NetCache)

[Note: the web URL shown in the FTP line is one of my ISP&#8217;s servers but they say they cannot explain what is happening]

---

### Post by soulestream on 2005-12-15
well. one thing is make sure UPnP is turned off in your router. This allows an appication to open/close ports as needed, which is an awful idea. Thanks M$. 

 Secondly your IP behind the router should not be a routable IP address. So either DHCP is really messed up, or it didnt get its IP from DHCP. I would be willing to bet the 98 machine isnt recieving DHCP broadcasts( or is ignoring them). That IP address was probably assigned by windows when it couldnt recieve an address. Check your network setting in the 98 Machine to see if that is actually is the IP of the machine. 

start -> run "cmd"  ipconfig -all    I think that is the process in 98, havent messed with it in a long time.

If the machine was open, shieldsup would have shown it. 


soule

---

### Post by dcstar on 2005-12-15
[QUOTE=soulestream]......
start -> run "cmd"  ipconfig -all    I think that is the process in 98, havent messed with it in a long time.
.......[/QUOTE]
"winipcfg"

---

### Post by stig on 2005-12-16
Thanks for the comments but I now have the solution. I too thought it would be the router and DHCP, but I was wrong.

After another hour in discussion with my ISP we found that the problem was due to proxy settings in my browsers on the Win98 machines. I have multiple browsers so that I can check my web pages display OK in them.

I don't recall ever setting anything for proxy servers in the browsers but they differed from browser to browser and from machine to machine! Those with proxy settings gave the problem scan results in Sygate - those without gave fully stealthed and the right (router) IP address.

So the answer was - switch off proxy settings or delete the settings in all the browsers.

And the best news of all is that it had nothing to do with adding Ubuntu PCs to my network and I can continue with my migration to Ubuntu (which is great!).

By the way, anybody with (like me) little or no knowledge of networks can easily set one up with Nautilus-Share:
[http://gentoo.ovibes.net/nautilus-share](http://gentoo.ovibes.net/nautilus-share)

---

### Post by davidsrsb on 2005-12-16
There are a few "vulnerability checkers" out there on the web that show internal IPs and are designed to scare you into buying firewall software.
They are actually getting your browser to run an asp or java application and there is no real security problem

---

