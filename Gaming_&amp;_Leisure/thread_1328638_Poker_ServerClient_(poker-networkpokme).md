---
title: "Poker Server/Client (poker-network/pokme)"
date: 2009-11-16
forum: Gaming &amp; Leisure
---

### Post by pzero on 2009-11-16
Hi everyone,

I am *attempting* to setup my own poker client/server setup for a few mates and random strangers to play on.  I know I could go and play at some of the commercial sites and I already do.  Figured setting up my own server would be a bit of an experience (and has been so far with many unsuccessful attempts).

I know that I could use pokerth-server or holdingnuts (even in Windows) but it does not give all the functionality I would like my server to offer (such as stud based games, ring games, multi table tournaments etc).  I even saw there was another poker server (windows based) from briggsoft (I think) that could do the job, but why pay $100US when there are open source alternatives.  I would rather donate that money to the open source project.

All that being said, I am wanting to setup the "python-poker-network" on Ubuntu 9.10 (32 bit) Server.  This would be a purpose built server so it would not have anything else on it.

So far I have done the following:

**SERVER**
installed the os
set static IP address
sudo apt-get install mysql-server
sudo apt-get install php5
sudo apt-get install python-poker-network

Are these all the packages I require? I am guessing that there are a few config files that I need to configure for the server.  I remember seeing poker.server.xml with generic values for the sql passwords etc


**CLIENT**

 I have not had a chance to fully look into [pok.me]("http://pok.me/"), but what config would I need to edit with that to connect to this server.  I would also like users to setup their own accounts (but I dont mind manually editing the mysql-tables to do so)



Has anyone set one of these up before? can anyone point me to some documentation for it, or pass on some tips?


I am happy to write up some doco so it helps others in the future.


Thanks all

---

### Post by richard015ar on 2010-04-03
[IMG]http://www.google.com.ar/images/cleardot.gif[/IMG]Mostrar forma romanizada
Hello, that it go with your project?
I tried to run poker-network with "jpoker" and I did work. I just do not know how to make it work on my server.
Tell me your experience, I still have not found a multiplayer poker game that is free.
Greetings!

PS: Sorry for my English so poor

---

