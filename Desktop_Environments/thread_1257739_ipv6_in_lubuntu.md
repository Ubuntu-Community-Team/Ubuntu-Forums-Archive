---
title: "ipv6 in lubuntu?"
date: 2009-09-04
forum: Desktop Environments
---

### Post by soloman498 on 2009-09-04
I have just downloaded lubuntu live disk and run it .everything works fine except the internet.It is showing that it receiving it but firefox keeps saying it can't find the server.I had this problem in Mandriva and I had to disable ipv6.How do I disable ipv6 in lubuntu?:confused:

---

### Post by Bucky Ball on 2009-09-04
in the firefox address bar:

about:config

Click 'I Promise!' then search for:

ipv6

You will find a line to disable it set to 'false'. Right click and 'toggle' that to true.

---

### Post by soloman498 on 2009-09-04
> **Bucky Ball said:**
> in the firefox address bar:

about:config

Click 'I Promise!' then search for:

ipv6

You will find a line to disable it set to 'false'. Right click and 'toggle' that to true.

 That was the first thing I tried but it didn't work unfortunately.
P.s. It is wireless internet and I have windows ME dual booted and it has no trouble with the internet.

---

### Post by hal10000 on 2009-09-04
First thing to verify if an internet connection can be established is to use the ping command:
In a terminal window try [COLOR="Red"]ping [www.google.com](www.google.com)[/COLOR]
If you get a positive answer, then your network works properly.
If you get nothing or something like "network is unreachable" then try 
[COLOR="Red"]ping 209.85.135.99[/COLOR]
(This is the ip-address of one of the google-servers)
If in the second case you get an answer and in the first case not, then it's likely that you have a nameserver problem.

How did you configure your network, dhcp or static ip?

---

### Post by soloman498 on 2009-09-04
When I pinged [www.google](www.google) .com the reply was Unknown Host.
when I pinged 209.85.135.99 the answer was network is unreachable.

the live disk was run over Antix mepis which I am useing to access this forum so it is not my wireless connection.I think it is dhcp :confused:

---

### Post by Bucky Ball on 2009-09-04
In System->Admin->Network check you have all the right details to match your router (if that is what you're using) and that your router is serving DHCP. 

ESSID and WEP or whatever type of security key you are using must match the router (you can copy these from your Windows setup). Configuration must be set to 'Auto-Config (DHCP)' and 'Enable Roaming' should be unticked for now. 

If you are trying to send a static IP from your local machine and the router is serving you one, it ain't gonna work so if you are using a static IP make sure your router is NOT serving an IP. Problem with this is that disables all machines getting served! So you can either change them to static also or just get served by the router.

If you are using a router, get into the config and check how that is setup if you don't already know. Try pinging the router itself on the LAN for the moment and just make sure you are connecting with that before pinging the WAN. :)

---

### Post by soloman498 on 2009-09-04
The computer I am trying the lubuntu live disk on is an old one out in the garage.It has windows ME dual booted with AntiX mepis (linux).The wireless network works on both but lubuntu live disk won,t pick it up.Could it be something to do with the live disk or is it ipv6 on the lubuntu live disk?

---

### Post by soloman498 on 2009-09-05
Well it,s not ipv6. I took the disk inside and tried it on my main computer (hard wired to the router) and the internet worked fine.So it must be that it doesn't like wireless.

---

### Post by Bucky Ball on 2009-09-05
Yea, you are going to need to set up wireless and I'm not sure if it is worth trying to do that from a Live CD. Now I get the picture of what you are trying to do. Wireless is rarely picked up just like that. You are going to need to download some drivers to get the card going and to do that you are going to need to plug an ethernet cable into the computer in the shed. A catch 22 situation. 

This won't come together on a live cd as you have nowhere to save the settings if you get me. You need to match the details in System->Admin->Network with your network and router details.

I'd take it inside, plug in an ethernet cable, get your updates and see if it picks up the card and offers you restricted drivers for it. Accept and set the correct details for you network and get wireless reliably working THEN take it out to the shed. 

You would find that the internet using the disk would work fine on the machine in the shed too ... if you had an ethernet cable plugged in so taking it inside and putting it in another computer unfortunately doesn't prove much. :)

Don't be confused because Windows is working. The two OSs have nothing to do with each other. You need to set the wireless up in Ubuntu. It won't automagically happen.

---

### Post by hal10000 on 2009-09-05
You should post the output of [COLOR="Red"]lspci[/COLOR] (if your wireless card is a pci card) resp. [COLOR="Red"]lsusb[/COLOR] (if you have an usb wireless card)

---

### Post by Bucky Ball on 2009-09-05
> **hal10000 said:**
> You should post the output of [COLOR=Red]lspci[/COLOR] (if your wireless card is a pci card) resp. [COLOR=Red]lsusb[/COLOR] (if you have an usb wireless card)

... and you are going to need to plug an ethernet cable in to do that, unless you make a file Windows can read and save to a partition Windows understands then copy/paste it here. It is definitely worth whipping the machine inside for a night. Then hopefully you will be pretty rock solid out there for a long time.

We have a thing about sheds in Australia. We love hanging out in 'em!

And hal10000: go Nanuck! Sling that yellow snowball!

---

### Post by soloman498 on 2009-09-05
Bucky Ball, I have a Linux distro (AntiX Mepis)working on the internet in the shed.I think I will wait until October when lubuntu 9.10 is released and try again.Thanks for your help):P

---

