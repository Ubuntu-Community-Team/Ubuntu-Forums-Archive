---
title: "Problem with vsftp"
date: 2009-05-07
forum: General Help
---

### Post by Richard1953 on 2009-05-07
I hope that I'm posting in the right place as this is the first time I've asked for help.
The problem I have is:- I've installed vsftp on my Kubuntu 6.06 system and set the config file to allow local login, the pc goes to the web via a usr 8004 and then to a cable modem to the ISP (Virgin). I can login to the server with [ftp://localhost](ftp://localhost) or [ftp://192.168.123.101](ftp://192.168.123.101) (the internal ip address of the pc) but... and this is the bit that confuses me I cant login using Konquerer or firefox using my domain ie ftp:// mydomain.net.
I have disabled the firewall on the router,and disabled firestarter and it just won't work :confused:
Please, somebody, give me a hint as to where I'm going wrong.

---

### Post by Alterax on 2009-05-07
Well, generally speaking you can't come in from your internal network using your external IP.  Now if you've tried from an outside connection and failed, then the problem is either the usr8400 is not forwarding inbound traffic to your computer (TCP 22 if using SFTP, TCP 20 and 21 if using standard FTP) or your cable modem is not passing all incoming traffic through to the usr8400.

To access the 8400, try running ifconfig to snag your gateway address, then opening that address in a webpage.  I'm not sure what your username and password would be for it, but if you didn't set that, grabbing the instruction manual for it online will probably provide you with the default logon.

To access the cable modem, check the 8400's configuration site (see above) and look to see what its gateway is...then go to it as a page.  Depending on who owns the modem, you may have to contact Virgin to have them set it to pass all traffic through.

---

### Post by Richard1953 on 2009-05-11
Hi Alterax,
I'm sorry for wasting your time, when I said that I had disabled the firestarter firewall, I was wrong. Over the weekend, I changed the settings to enable ports20/21 to be allowed through and this is the important bit - APPLIED the rule. It all then worked as it should!!!
Thanks for the advice - and as they say you learn something new every day.:o

---

