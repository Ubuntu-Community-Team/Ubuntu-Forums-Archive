---
title: "internet connection"
date: 2006-01-06
forum: General Help
---

### Post by Strannik on 2006-01-06
Hello everybody...I installed ubuntu at home and i don't know how to do one thing:
How can i connect to the internet through my LAN. IN winxp i create my connection like this:
Network Connections > Create new connection > Connect to the Internet > Setup the connecton Manually > Connect to broadband connection that requires a username and password. 
How can I make this type of internet connect in Ubuntu? Which application should I use??? With everything else Ubuntu is ok with me but can't connect to internet from home...

---

### Post by Ocxic on 2006-01-06
got to system->administration->networking that will allow you to setup your net connection

---

### Post by Strannik on 2006-01-06
my network works fine. i can't connect to the internet (because i don't know with wich tool i can do it)

---

### Post by handy on 2006-01-06
Hi,

Have a look at the link below, scroll down to the **_Internet Stuff:_** section.  That's what I had to do to connect, It's not hard, but when your new it takes a while to get the know how, & that's even with this magnificent forum...  :KS 

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

All the best.

handy

---

### Post by s_spiff on 2006-01-06
do u use pppoe?

---

### Post by Strannik on 2006-01-06
[QUOTE=s_spiff]do u use pppoe?[/QUOTE]

really...i don't know =) i looked through what google gave me and it looks like it is exactly what i need. Could somebody point me in the right direction on how to use it. Is there any front end in ubuntu for it?

---

### Post by Strannik on 2006-01-06
i found this on the forum> [http://ubuntuforums.org/showthread.php?t=110480&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=110480&highlight=pppoe)
will try it at home. does anybody have any other ideas?

---

### Post by healychan on 2006-01-06
Are you using router to share internet?? If yes, does you router support DCHP??

post the result of "ifconfig" please.

---

### Post by Strannik on 2006-01-06
i will post the results of ifconfig as soon as i get home

---

### Post by Strannik on 2006-01-08
Everybody thanks...i just didn't know that I needed pppoe....(i never even knew that it existed :D ) i tried pppoeconf and everything works just great now. Thank you everybody for your help...you guys are great...

---

