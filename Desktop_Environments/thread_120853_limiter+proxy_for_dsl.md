---
title: "limiter+proxy for dsl"
date: 2006-01-23
forum: Desktop Environments
---

### Post by madmetal on 2006-01-23
hello!
i am going to share my dsl connection using an old pc ( PIII 450 /128ram /20gb) i am thinking about using ubuntu and i am searching how am i going to use limit bandwidth using IPs
the network will be 

dsl
| 
pc(ubuntu) - wireless ap- pc2 (lan) pc3 (wireless)
|
pc1(lan)

as far as i have read i shall use wondershaper for traffic shaper and firestarter for firewall gui but i haven't found somewhere how can i control the bandwidht using IPs.
 



i want pc1 to have 2/4 of b/w and pc2/pc3 have 1/4 of b/w each 
wondershaper has also a b/w limiter?
thanx to anyone answers ( i am a real noob linux user)

---

### Post by madmetal on 2006-01-25
any help with usefull [-o< 
thanx! :)

---

### Post by cwaldbieser on 2006-01-26
[QUOTE=madmetal]hello!
i am going to share my dsl connection using an old pc ( PIII 450 /128ram /20gb) i am thinking about using ubuntu and i am searching how am i going to use limit bandwidth using IPs
the network will be 

dsl
| 
pc(ubuntu) - wireless ap- pc2 (lan) pc3 (wireless)
|
pc1(lan)

as far as i have read i shall use wondershaper for traffic shaper and firestarter for firewall gui but i haven't found somewhere how can i control the bandwidht using IPs.
 



i want pc1 to have 2/4 of b/w and pc2/pc3 have 1/4 of b/w each 
wondershaper has also a b/w limiter?
thanx to anyone answers ( i am a real noob linux user)[/QUOTE]

Can you give an example of what you mean?  I am having a little trouble understanding what you mean by "control the bandwidth using IPs."  What does "IPs" stand for in this case?

---

### Post by Ocxic on 2006-01-26
why would you want to limit your bandwidth for the other computer?

---

### Post by madmetal on 2006-01-27
thanx for your interest.

the ubuntu pc will share dsl line through wireless and wired lan so 2 of the other computers wont be on any eth port of ubuntu/
the solutions i have seen till now is to control bandwith using eth0 eth1 etc.


ocxic in order to be everyone happy and satisfied there must be some kind of control at the bandwidth( other computers= other users)

---

### Post by Horndog on 2006-01-27
Have a look [here.]("http://www.google.com/search?hl=en&q=limit+bandwidth+linux&btnG=Google+Search")

---

### Post by Ocxic on 2006-01-27
but limiting the bandwidth will just make everyone slower. if not only one person/computer. if you were to just leave it then everyone on your network would be able to use the maxamum amount of bandwidth at any time. limiting the bandwidth will not giva a performance boost to anyone, it just makes the ppl who you are limiting the bandidth too go slower, why not utalize the full power of your internet connection for everyone to share. this is how i have it at my house, using a router, me and my dad are both connected to a D-Link DI-604 and iether of use may use may use all of the available bandwidth at any time, and when we are both using the net at the same time, it automaticaly balances out the load and depending on what iether of use is doin at the time may cause one of our computers to run slower. ex: when my dad is using his webcam i can't use azureus to dowload torrents, it will "clog" the connection cause he is usein so much of the bandwidth, yet me surfing in firefox while he is doing this is not noticably affected, and visa versa.

---

### Post by nix4me on 2006-01-27
You should check out lartc.

google it.

nix4me

---

### Post by madmetal on 2006-01-27
nix4me and horngod than for suggestions i have a long way to go reading..

ocxic my problem is a little more complex cause the computers using the net will be at different houses and we should make rules how to use it...

the only thing that i will definitely  use is squid -hope proxy will help a little at least for the http part-  and i point if any problems occur.

:-D thanx!

---

