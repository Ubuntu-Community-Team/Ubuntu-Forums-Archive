---
title: "internet connection problem pppoe"
date: 2009-03-08
forum: General Help
---

### Post by zappa98 on 2009-03-08
This is my problem :
i have a DNS fiberlink connection , normally (on win XP) all i have to do is click on icon on the desktop -> small screen requesting user and password ->CONECTED.
i've looked at my network connection to see what kind i have it says i have "point-to-point protocol over ethernal pppoe" says its broadband connection...
anybody know how do i set up the connection , i NEED my net 

this what i have:
[http://img237.imageshack.us/my.php?image=networkconnection.jpg](http://img237.imageshack.us/my.php?image=networkconnection.jpg)

and 

[http://img10.imageshack.us/img10/6113/networkconnection2.jpg](http://img10.imageshack.us/img10/6113/networkconnection2.jpg)

anybody know how ?

P.S. please if you know dont give me a "ahh , easy just reroute the doodah with the gateway uber-modulator gizmo by using a super high level algorithm " answer

---

### Post by zappa98 on 2009-03-08
also i found that i have dynamic IP

---

### Post by agilius on 2009-09-17
Hi zappa, I am also a RDS user just like you and I am stuck with no internet connection on Linux from them. I think it's ISP related.

Things that I did:

[I am new to linux so I don't know all the terms]

1) Tried to recreate the connection from the network panel - did not work
2) I tried to connect manually via the terminal with pppoeconfig, followed all the instruction that you might already have found on this forum. - did not work
3) Tested to see how the connection was going after using pon dsl-provider and along the lines I got "Authentication Failed". My password and user name are correct. - did not work
4) I reinstalled linux. - did not work
5) I log into windows.. I got connected... I posted this message - it worked :) 
6) I went back to linux - It didn't work...

I hope that someone would share a few thoughts about this. Thanks in advance.

EDIT: I did it! I don't know how exactly but here is what I did:

1) I ran pppoeconf again 
2) Added the password and the user, press enter all the way to the end
3) I made sure I had an ip address assigned by typing sudo plog... 
```
Sep 17 17:09:49 agilius-laptop pppd[5363]:** local  IP address 188.24.19.197**
Sep 17 17:09:49 agilius-laptop pppd[5363]: remote IP address 10.0.0.1
Sep 17 17:09:49 agilius-laptop pppd[5363]: primary   DNS address 193.231.252.1
Sep 17 17:09:49 agilius-laptop pppd[5363]: secondary DNS address 213.154.124.1

```4) I went up to the right corner of my screen, and connected to the basic Ethernet connection (Auto Ethernet). If you don't have this, just delete the default Auto-E1 wired connection by right clicking that icon and choosing edit connection.
5) I googled something and it worked!

EDIT AGAIN: 

The steps that I followed last time worked only for on login session. After I restarted the computer, the Auto Ethernet was no longer there and I had to try something else. 

Out of luck I managed to do this again:

1) I remade the pppoeconf and chosed NO when I was asked to save the DNS servers automatically. 
2) I connected and it seemed it work. 
3) I noticed that I got disconected after a short while, I simply used poff dsl-provider, then poff, then pon dsl-provider again. After this I had no problem at all untill the next restart.
4) On a romanian forum I found this little guide:

PS: Since you are using RDS, I think you can understand romanian:

> pentru a rezolva problema cu deconectarea trebuie sa urmezi urmatorii pasi: 
 
1. deschizi terminal si scrii: 
CODE 
sudo pppoeconf 
 
completezi ce iti cere "wizard-ul"(username,pass, etc-cele date de RDS) 
 
2.apoi browse pana la /etc/ppp/peers/dsl-provider 
si inlocuiesti 
CODE 
lcp-echo-interval 30 
lcp-echo-failure 4 
 
cu 
CODE 
lcp-echo-interval 0 
lcp-echo-failure 0 
 
 
asta ar trebui sa rezolve problema...succes. 

So simply set interval to 0 and faliure to 0. I have no idea what this does exactly, but now I just open my connection via sudo pon dsl-provider or I log in as root and I have a steady connection. 

If you can't edit the file that is mentioned in the guide, simply log in as root or use gksudo nautilus in terminal to get access to the peers folder.

---

