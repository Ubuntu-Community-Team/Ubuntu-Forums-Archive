---
title: "Gaim - Problem getting conected."
date: 2006-05-16
forum: Desktop Environments
---

### Post by simbiwa on 2006-05-16
I am connected to the network via a LAN card (Ethernet 0).  I have no problem browsing the net but what do I have to do to configure in Gaim to get connected? My service provider is running an ISA server in Windows.

I tried to connect through Gaim to Yahoo messenger and Msn messenger but it gets stuck at connecting......

What ports do I have to use? I have tried http, socks4, socks 5 with the combinations of ports 1080, 8080, 80, 139 but nothing seems to work.

I am having this problem of messengers not getting connected in all the Linux distros, I have tried Mepis, Ubuntu, and even Red Hat but Win Xp connects easily. Is it because my service provider's server is running on Xp??

I would really appreciate if anyone can guide me or point to some website where I can figure it out.

---

### Post by Scunizi on 2006-05-16
If you have a router try opening the DMZ to the computer you're using just as a test.  You really don't want to leave DMZ open.  If it connects fine then you might visit Yahoo's site and/or MSN's to find out what the port requirements are.  Gaim for me will occationally get stuck on Yahoo but MSN always works.  When it does get stuck I can usually connect by opening the Gaim window and doing a control A.  That will bring up your account box and you'll see that the service that didn't load doesn't have a checkmark under "Online".  check the box and it will try to connect again.

---

### Post by DarkStarDeity on 2006-05-17
I had a similar problem with Gaim not connecting to Jabber (IIRC, it connected to ICQ and MSN OK), and couldn't be bothered farting about with it so I just installed Psi, which is what I used on Windoze anyway and all was good. So if you can't get Gaim sorted I'd recommend giving Psi a try. You'll need to sign up for a Jabber account (free) at a server that has MSN and Yahoo gateways. There's a list of servers and the gateways they support [here]("http://www.jabber.org/network/oldnetwork.shtml"), although it is an old list and may be out of date, there is another list of public servers (without the supported gateways info) [here]("http://www.xmpp.net/bycountry.shtml").

---

### Post by mosestruong on 2006-05-19
I've just started having problems connecting to MSN and AIM/ICQ, but Yahoo works. If I use MSN Messenger, I can connect without any problems except that I have to boot into windows. 
Would anyone know what might cause this?

---

### Post by burnt on 2006-05-23
I had trouble connecting to MSN Messenger with Gaim, but I was able to connect by doing the following.

In the accounts menu, I chose the msn messenger account and clicked 'modify'.

Then I clicked on 'show more options' near the bottom of the window.

I checked the 'Use HTTP Method' box.

Now I'm able to connect.

It worked for me, but I don't know why it worked.

---

### Post by true_friend on 2006-08-08
behind an ISAserver u can not connect to internet without NTLM proxy server. it is a linux based software which decieves the ISAserver as the requests are from IE. but it supports only HTTP requests.i have also the same problem can no connect to internet from linux box i am also behind ISAserver. can browse and download because they work with HTTP but messenger's request are not HTTP requests. so u have to convert them to HTTP. u can use ["socks via http"]("http://lightbox.ath.cx/socks/") a software supports ["NTLM Proxy Server"]("http://www.geocities.com/rozmanov/ntlm/"). it converts sokcs request to http then they are tunneled throught NTLM PS. but i could not configure it with NTLM. the settings are complicated and there is no guide availabale.
For browsing behind ISA server [try this]("http://www.linux.com/howtos/Web-Browsing-Behind-ISA-Server-HOWTO.shtml#toc1")

---

