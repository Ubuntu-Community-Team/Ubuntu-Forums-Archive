---
title: "wondershaper / traffic shaper"
date: 2005-05-17
forum: Desktop Environments
---

### Post by cusco on 2005-05-17
Hi all... I donwloaded wondershaper from apt and I would like to know if there is a possible way to shape the traffic ONLY in certain ports (3990 3991 and 3992) as wondershaper shapes all the traffic!

even tho I can set those ports as low priority.. its not enough...


I have other people on my internal network from whom I cannot steal much bandwidth 

I have huge amount of outgoing traffic in 3990 and 3991

if I shape with wondershaper to have like only 100 bits traffic.. irc starts lagging.. and other connections as well...

so I would like to impose limits on outgoing traffic ONLY on port 3990

thanks in advance

---

### Post by Rodrigo on 2005-05-17
mmmm, that sounds like you need to use a more advance solution, that is... a proxy... yup Squid will do (yeah!, woohoo  ;-) )
You see, squid can restrict ports, and traffic on them. So that will be a perfect solution. Sadly its kind of complicated (all powerfull things are  :razz: )...
good luck

---

