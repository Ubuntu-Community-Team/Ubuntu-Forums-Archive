---
title: "internet?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by x__dark on 2005-08-12
Okay, I just finsihed building my computer the other day. Nothing impressive, but I needed to get away from the family PC. Well, a month or so ago, a friend of mine suggested Kubuntu Linux over MS Windows. So i took him up on the offer today and downloaded the install disk. I installed Kubuntu fresh on my brand new PC. Everything went smooth until I plugged in my cable modem. I have no IDEA how to get the modem to work. I thought it was the drivers at frist, because I didn't install the drivers for my mobo, they were all for windows, but it seems everything was reconized none the less. I'm using a RoadRunner Cable connection. Any thoughts/help/ways out of this mess to get on the internet?

---

### Post by Digitallysick on 2005-08-12
it should auto pick it up, try rebooting the pc, i have kubuntu and road runner, and mine picked up automaticlly

---

### Post by x__dark on 2005-08-12
Could it be that I didn't install the drivers? I keep coming back to this issue. Gar. . lol Long day, getting edgy. haha.

---

### Post by emperor on 2005-08-12
Buy an inexpensive hardware cable/DSL router and connect the cable modem to the router and your PC to the lan connection on the router.

---

### Post by x__dark on 2005-08-12
[QUOTE=Digitallysick]it should auto pick it up, try rebooting the pc, i have kubuntu and road runner, and mine picked up automaticlly[/QUOTE]

I tried this, it just will not let me on the internet. I'm getting pissed. lol

---

### Post by varunus on 2005-08-12
Can you post the output of lsmod and lspci in a terminal?  Also the output of "ifconfig" and "route -n" in a terminal.  (so we can see your settings.)

---

### Post by palsyboy on 2005-08-12
[QUOTE=emperor]Buy an inexpensive hardware cable/DSL router and connect the cable modem to the router and your PC to the lan connection on the router.[/QUOTE]
I second that.  Everyone should have a router/firewall anyway.

---

### Post by dr1445 on 2005-08-12
i am in mepis just now, but as i recall try K>systems>network, and see if you can configure the net card. that should get etho0 up and running.

---

### Post by Tinuz on 2005-08-12
[QUOTE=x__dark]Could it be that I didn't install the drivers? I keep coming back to this issue. Gar. . lol Long day, getting edgy. haha.[/QUOTE]
Hmm, i dont think a cable modem needs drivers. Usually they are just a way of entering the providers network and your computer sees them as little more than a LAN(it recognizes that it is a WAN and that it can be used for internet). 
Do the following:
Start up the Konsole('Start'->System->Terminal program(Konsole))
Type in Ifconfig
This displays a list of characteristics of your current ethernet hardware/connections
If there is no networkcard recognized you should only see 'lo' printed on the left side of the Konsole. If there is a viable ethernet card, there should also be an 'eth0'(or higher number if you have more than one ethernet card enabled) listing. 

If there is not, your drivers are not correctly configured, this can be done by loading the correct driver. However, the last time i have done this was when the dinosaurs still ruled the earth  ;-)  so consult someone else on this.

If it is there, your protocols are not correctly set, this can be as easy as simply DHCPing your connection and how to can be found in the FAQ ([http://www.frankandjacq.com/ubuntuguide/5.04/index.html)](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)). (But again, i have had very few problems with ethernet, so i do not know all ins and outs). 

If these two approaches do not solve the problem, i'm at a loss too  ;-) 



I

---

### Post by x__dark on 2005-08-13
> **Tinuz]Hmm, i dont think a cable modem needs drivers. Usually they are just a way of entering the providers network and your computer sees them as little more than a LAN(it recognizes that it is a WAN and that it can be used for internet). 
Do the following:
Start up the Konsole('Start'->System->Terminal program(Konsole))
Type in Ifconfig
This displays a list of characteristics of your current ethernet hardware/connections
If there is no networkcard recognized you should only see 'lo' printed on the left side of the Konsole. If there is a viable ethernet card, there should also be an 'eth0'(or higher number if you have more than one ethernet card enabled) listing. 

If there is not, your drivers are not correctly configured, this can be done by loading the correct driver. However, the last time i have done this was when the dinosaurs still ruled the earth   said:**
> http://www.frankandjacq.com/ubuntuguide/5.04/index.html)[/url]. (But again, i have had very few problems with ethernet, so i do not know all ins and outs). 

If these two approaches do not solve the problem, i'm at a loss too  ;-) 



I
 Thanks, I'll give it a shot in the morning. I'm pretty tired at the moment.

---

