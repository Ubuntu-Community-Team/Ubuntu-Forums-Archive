---
title: "Network ports"
date: 2006-02-20
forum: Desktop Environments
---

### Post by ccarrillo on 2006-02-20
Hello everybody, sorry if this question was submitted before but really I didn't found any howto or documentation about this... :)... maybe I'm just searching in a bad way

I just found out with nmap that the ports I need to use are closed, 

could anyone help me how to just simply open tcp or udp ports?

Thanks very much and the best regards,

Carlos

---

### Post by steve.horsley on 2006-02-20
What ports do you need, and why? What application are you wanting to use? The ports are probably closed because there is no application listening on them.

---

### Post by ccarrillo on 2006-02-21
Yes, I understand what you mean...

I would like to know the way to open the tcp and udp ports, but let's say for the amule...

Thanks very much in advance, rgds,

---

### Post by jones_jj on 2006-02-21
Do you have a firewall running in Ubuntu, like firestart (not sure of the name) or a firewall running on a router that you are using?

Personally I would not use amule, it is nothing but a giant virus/trojan/worm from what I remember of it.

---

### Post by ccarrillo on 2006-02-22
Hey, thanks

No, actually without using any firewall, i tried to use cisco vpnclient without success, i found that the ports should be open. So that's why I'm looking why to open the ports, so then I used firestarter and I didn't got any result because I really don't know how to configure it, I know this sounds silly :P...!!!! But I tried without success adding rules to the ports required!! 

Also I'm using a cable modem, and I don't know if it's neccessary to change something in the router...

Thanks in advance and rgds,

---

### Post by jchau on 2006-02-22
Your problems with the network ports are probably caused by the server you are trying to connect to.  Your program should open ports for itself as necessary (esp. w/o a firewall).  If you open the port, you may cause even more problems since the actual program using the port will be unable to use the already taken port.

---

### Post by jchau on 2006-02-22
Oh, if you're behind a router, you probably have to tell the router to foward the appropriate ports.

---

