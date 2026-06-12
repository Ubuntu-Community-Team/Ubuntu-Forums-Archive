---
title: "what is my REAL IP?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Redeyes_Gambit on 2006-02-20
}{i,

I am confused about something, if I am behind a router and my personal machine's IP is designated by DHCP, and yet I want to connect to one of the machines in my home network via VNC from somewhere OUTSIDE of my home network, how would I do that? 

Is there a "real" IP address other than the 192.168.2.1.... (network address assigned by DHCP) that I can use to connect to a specific machine in my home network from outside my home network? If so how do I find it? If not is there some work around?

thnx!

---

### Post by dickohead on 2006-02-20
You would connect to the address of your router, commonly known as your Internet IP, or Public IP. But you would also need to setup port forwarding so that when your router receives the request on the ports for VNC it can forward them to the correct computer, just as forwarding port 80 to a web server gives you a web page at your public IP.

---

### Post by openmind on 2006-02-20
I think if you type "ifconfig" in aTerminal it'll give you your IP address right?

If not someone with more knowledge can put me right.

---

### Post by larsemil on 2006-02-20
yes there is one public ipadress. that adress probably goes to your router. 

here is what to do:
1. find out your ip (visiting [www.whatsmyip.net](www.whatsmyip.net) should do the trick)
2. enable port forwarding on your router(if the vnc has port 6000 enable port 6000 on the router and forward it to your local ip)
3. enjoy!

---

### Post by larsemil on 2006-02-20
[QUOTE=openmind]I think if you type "ifconfig" in aTerminal it'll give you your IP address right?

If not someone with more knowledge can put me right.[/QUOTE]

that would only show the local ip.(192.168. blaha blaha)

---

### Post by kelloggsx on 2006-02-20
hmm

how about [http://www.ipchicken.com](http://www.ipchicken.com)


:-) hope it works

---

### Post by KurtB on 2006-02-20
In your setup ( Internetmodem - router - PC) ther will be 2 IP-addresses:

* The one your PC gets from the router -> the 192.* IP, if you type ifconfig you will most likely get this IP as a result.

* The one your router receives from your ISP -> use Firefox, surf to your gateway (use ifconfig or the manual of your router. Most routergateways are 192.168.1.1 or 192.168.2.1 depending on manufacturer) which will open the interface of your router. There you will see your WAN-side IP address, which is the IP-address of the ISP.

kind regards,
KurtB

PS: I thought that using a site like [http://www.whatismyip.com/](http://www.whatismyip.com/) also returned the "real" IP-address of your ISP

---

### Post by Wallakoala on 2006-02-20
go to one of those websites which tell you what your ip adress is. My fav is [www.ipchicken.com](www.ipchicken.com)
there is also a [www.whatismyip.com](www.whatismyip.com)

---

### Post by Redeyes_Gambit on 2006-02-20
WOW! That was fast. I was figuring I would have to wait a day or two to get this resolved. Many thanks to all you guys!

Unfortunaly I am probably setting up my router and modem wrong. I may mess around with it a bit more, but for now I thank you guys for your help!

---

