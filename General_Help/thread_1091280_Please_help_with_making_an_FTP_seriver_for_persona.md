---
title: "Please help with making an FTP seriver for personal file sharing"
date: 2009-03-09
forum: General Help
---

### Post by mahela007 on 2009-03-09
I have googled for hours and got nothing. Can someone please outline the basic procedure of making an FTP server on KUBUNTU? From what I have read the easiest one to set up is VSFTPD so I would like instructions which would help me with setting it up.
My Kubuntu PC is connected to the internet via a router. I haven't done any special configuring or anything.
I would like to set up my FTP server so that only Ican access it in order to  use my files when I'm not at home.

---

### Post by stevanbt on 2009-03-09
Hi,
Is this what you're looking for?

[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)

Thanks, Steve.

---

### Post by mahela007 on 2009-03-09
hmm. I'll check it out. Thanks for your reply

---

### Post by mahela007 on 2009-03-09
hmm... It doesn't say what I should do if I am behind a router

---

### Post by HermanAB on 2009-03-09
FTP has a problem with routers.  You need to do three things: You need to forward port 21 TCP to your machine. Your machine must have a static address for that to work and the router must have a FTP tracking module.

If the router runs Linux, then it should be able to do FTP tracking.  If not, then you need to forward ALL ports to your machine, by using the router DMZ feature.

However, bear in mind that FTP is insecure by design, so it is better to install ssh-server and then only forward port 22 TCP.  The FileZilla client program can do SSH/SFTP and is cross platform.

Cheers,

Herman

---

### Post by mahela007 on 2009-03-09
WOW! I don't really know what all this means. More specifically what is "forwarding ports"?

---

### Post by tsucol11 on 2009-03-09
Filezilla server is for windows only.

Brian

---

### Post by mahela007 on 2009-03-09
Huh? I just saw on their website, they have a linux version.

---

### Post by Slim Odds on 2009-03-09
Definitely, use an ssh server.

---

### Post by aesis05401 on 2009-03-09
> **mahela007 said:**
> WOW! I don't really know what all this means. More specifically what is "forwarding ports"?

Packets coming from the WAN hit your router and are then redistributed to the LAN or dropped.  

If you set your PC to a static LAN IP address, then set your router to send a particular type of traffic received from the WAN to that IP address you have forwarded a port.  The path is from the WAN through the router to the destination LAN address... your FTP server.  

There are more considerations than just port forwarding.  Any LAN filters or firewalls may interfere with operation of an FTP server - look there first if you set up forwarding but don't see activity at the destination LAN IP address.

Edit: I should mention that forwarding usually doesn't require anything crazy on the router side of things.  There is usually a table for forwarding.. add a new destination and choose the port or protocol to forward, sometimes a router soft-reset is required afterward.

---

### Post by mahela007 on 2009-03-10
> **aesis05401 said:**
> Packets coming from the WAN hit your router and are then redistributed to the LAN or dropped.  

If you set your PC to a static LAN IP address, then set your router to send a particular type of traffic received from the WAN to that IP address you have forwarded a port.  The path is from the WAN through the router to the destination LAN address... your FTP server.  

There are more considerations than just port forwarding.  Any LAN filters or firewalls may interfere with operation of an FTP server - look there first if you set up forwarding but don't see activity at the destination LAN IP address.

Edit: I should mention that forwarding usually doesn't require anything crazy on the router side of things.  There is usually a table for forwarding.. add a new destination and choose the port or protocol to forward, sometimes a router soft-reset is required afterward.

Thanks A LOT! This is exactly what I was looking for.

---

### Post by mahela007 on 2009-03-10
Um.. why does port forwarding require my computer to have a static IP address? (it does require this right?) 
similarly does my router also require a static IP address?

---

### Post by Slim Odds on 2009-03-10
> **mahela007 said:**
> Um.. why does port forwarding require my computer to have a static IP address? (it does require this right?) 

Yes..... How else will the router know where to send the data?

> similarly does my router also require a static IP address?Your router already has a static address (usually something like 192.168.1.1)

---

### Post by mahela007 on 2009-03-11
thanks.
but that static address is only on my local network right? What about access from the internet?

---

### Post by rhconcepts on 2009-03-11
This is one thing I can help out with lol. In your router settings make sure your sever is always getting the same ip like 192.168.1.25 if you don't have it set up right it could pull a different one when you reboot. Go into your router and look for Use Router as DHCP Server and set the server up to pull the same ip every time. Also look for port forwarding, and make sure 21 is forward to the ip you set for the server. Now on the other side if your isp gives you a different ip all the time your going to have a hard time. You will need to know that ip to get to the server. I have comcast and they change my ip maybe once a year, not bad.

Im trying to do the same as you but with ubuntu desktop. Let me know what you use to run the ftp. Thanks

---

### Post by mahela007 on 2009-03-11
> **rhconcepts said:**
> This is one thing I can help out with lol. In your router settings make sure your sever is always getting the same ip like 192.168.1.25 if you don't have it set up right it could pull a different one when you reboot. Go into your router and look for Use Router as DHCP Server and set the server up to pull the same ip every time. Also look for port forwarding, and make sure 21 is forward to the ip you set for the server. Now on the other side if your isp gives you a different ip all the time your going to have a hard time. You will need to know that ip to get to the server. I have comcast and they change my ip maybe once a year, not bad.

Im trying to do the same as you but with ubuntu desktop. Let me know what you use to run the ftp. Thanks
ok.. thanks for your help

---

### Post by aesis05401 on 2009-03-13
> **rhconcepts said:**
> *snip*... Now on the other side if your isp gives you a different ip all the time your going to have a hard time. You will need to know that ip to get to the server... *snip* 

The solution that I see recommended most often is to use a 'dynamic dns' service.  Some of these services are free, but I think they all require you to run scripts on your server or at least the LAN on which the server resides.  

Presumably these scripts are pushing your current WAN IP address to the dns lookup provider - allowing you to get to your server via their routing instructions.  I have no idea how reliable any of those providers are...  

Threads on this topic exist all over the web, though, so goodnight ;)

---

