---
title: "Bypassing packet filtering"
date: 2006-03-25
forum: Gaming &amp; Leisure
---

### Post by aLT Wizard on 2006-03-25
Hello everyone!
Im a new member here ( Joint the forums long back actually! ) , I've been using ubuntu for about 3 months though , I love it :D :D , I also hope Im posting this thread in the right board, so forgive me if I dont :) 

I have a very crappy ISP  which is monopolistic here, They have some kind of packet filtering done in order to reduce the bandwith I use , this is against their terms of contract, but there is nothing I can do about it ! , Because of this filter , Every Multiplayer game I play gives me High Ping times (over 500ms On canada servers) , My Friend who lives in a nearby country gets pings of about 10-200ms max on those servers . The Network Genius's here tell me that there are methods of bypassing the packet filtering by tunneling all my data through a faster port that they do not filter such as ssh , Now I have no idea what that means ](*,)  , They wouldnt even tell me what they meant , They think they are too gr8 , But they dont know I have the gr8 Ubuntu Community to help me with this :D :D , So please help me bypass this filter!

aLT Wizard.

---

### Post by ZylGadis on 2006-03-25
Your case would require cooperation from both ends of the connection. This means that you are stuck there, unless you can convince the administrator of a game server to make special arrangements for you.
Alternatively, you can use a third machine like this:

A - connect over non-filtered port - B - normal conn - C

where A is your home machine, B is the third machine which lies outside of your ISP's monopoly, and C is the game server. Once you have found machine B, you will need to install there a small program, called a "bouncer", which would simply forward any ip packets back and forth between A and C.
Bear in mind that your total ping time to the game server would be the sum of all relevant times. I doubt you'll get much out of such a connection.

---

### Post by aLT Wizard on 2006-03-26
can u tell me where to get such a server that will allow me to run bouncer?

---

