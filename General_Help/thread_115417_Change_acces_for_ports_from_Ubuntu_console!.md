---
title: "Change acces for ports from Ubuntu console!"
date: 2006-01-10
forum: General Help
---

### Post by rensu on 2006-01-10
My problem is this:
I want to open all ports on router and close them with iptables. How would that be possible? My router is Prestige 660HW-61. Im really bored to always call a guy to tell him that open that port and that port. I would be very happy if we could find a way to open and close ports from console. Any ideas?:confused:

---

### Post by rensu on 2006-01-14
No ideas ?:S

---

### Post by kosmic on 2006-01-14
Why do you want to open all port in your Router ?? is not a very wise move.
 
YOur router should have a web based configuration utility, try open a firefox and in the URL write - [http://192.168.1.1]("http://192.168.1.1") and see if it works :)

---

### Post by rensu on 2006-01-15
Because I have access to the linux server only. Router is in other place.

---

### Post by kosmic on 2006-01-15
Does your router don't have a WEb based acess to the configuration ? because the only way I see you can open the ports in the router is One by one :(

---

### Post by rensu on 2006-01-15
Actually the server & router is in other place. I use SSH for logging into server and confing it. I that's why i need to forward all ports to linux and change the accesses from there with iptables or something like that.

---

### Post by kosmic on 2006-01-15
In some routers in the NAT options there is an option to open a number of ports like 1 - 566000 to a specific IP. Some one it access to the configuration of the router should go to the NAT configuration and see if this router as this option.
 
Also you can look in the Option of the router that as something writen like this : Port Forward

---

### Post by rensu on 2006-01-15
But any infos if I can put the web configuration on any other port? Because I have my apache running already on port 80.

---

