---
title: "How to connect 2 Ubuntu computers for gaming?"
date: 2014-03-31
forum: Gaming &amp; Leisure
---

### Post by gabmuks on 2014-03-31
Hello and good day.

Would like to play Warzone 2100 with my son.
I have two wifi computers connected to my home router.
Is there a way for them to communicate through my router to play games?

Thank you for your time.

---

### Post by mastablasta on 2014-04-01
yes. the one with the server might need to open the port for the game. you could use GUFW for that if necessary.

otherwise have you tried connecting the computers to eachother? create game server (probably listen server) and then connect to it from the other computer using the IP assigned by router.

---

### Post by gabmuks on 2014-04-13
> **mastablasta said:**
> yes. the one with the server might need to open the port for the game. you could use GUFW for that if necessary.

otherwise have you tried connecting the computers to eachother? create game server (probably listen server) and then connect to it from the other computer using the IP assigned by router.
Thank you for kind reply.

Might there be an explanation of the server method of connecting the two?

I have never done that before. Would not know where to start.

Thank you for your time

---

### Post by mastablasta on 2014-04-16
let's say with GUFW - have a look here: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

you need to allow outgoing and incomming connection on the port the game uses (see games server documentation on that). user connecting to server also may need a port open at least to receive data through it.

usually routers will allow computers to connect with eachother if they are in LAN (as in your case).

However if a port needs to be forwarded on router the procedure is similar. you need to know what port and protocol the game uses (suualyl in theri server documentation) and then you open that port on router. each router does that differently but there are sites on internet that have many models listed and procedures on how to do it. for example one of them is portforward.com: [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)
you need ot knwo router model and then search for a guide on how to do it. usually it's very simple once you know where to look.

you can also asign a range of ports to be opened but that is not advised unless game needs them. 

sorry i can't be more specific as i haven't played this game (yet).

---

### Post by dannyboy79 on 2014-04-17
you're making this way harder than it needs to be, Ubuntu doesn't have any ports blocked by default, so as long as both computers are on the same LAN than all you need to do is on either computer tell it to "host" a local game. On the opposite computer you would just join the game of the computer that's hosting the game. since you're not connecting to anyone outside your LAN there's no need to forward ports or anything like that.

---

