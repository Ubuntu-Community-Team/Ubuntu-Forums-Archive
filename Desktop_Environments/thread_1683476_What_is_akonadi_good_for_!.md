---
title: "What is akonadi good for ?!?"
date: 2011-02-07
forum: Desktop Environments
---

### Post by dargaud on 2011-02-07
Hello all,
I'm not trolling here, I really want to know what's the point of Akonadi. Do I use it without knowing ? Trying to read about it only leads to a brain cramp: "Akonadi is a storage service for personal information management (PIM) data and metadata". Huh ?!?

The reason I'm asking is that I often want to run kmail remotely through X. I get an extra window that says "Akonadi Server self-test", and if I close it, it kills Kmail... What consequences if I remove it ?

---

### Post by nick_goodfate on 2011-02-07
Reading [this]("http://en.wikipedia.org/wiki/Akonadi") i understood that it's the program that takes care of the communication between some of your applications like kmail with the the rest of the network. 
"Akonadi communicates with servers to fetch and send data instead of applications through a specialized API."

---

### Post by ubuntu27 on 2011-02-07
Ah.. oh no. I experienced that before. It seems that there are no fix for it yet.

Here are the bug reports:

Bug#619387 [kmail crashed with Akonadi Server Self-Test Report]("https://bugs.launchpad.net/debian/+source/akonadi/+bug/619387")  

Bug#608154 [MySQL bug(s) crash akonadiserver]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/608154")

Bug#578357 [MySql log file problem prevents Akonadi startup]("https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/578357")

Bug#604669 
[akonadi-based address book stops working (server crash?)]("https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/604669")


Add yourself to the people who are experiencing the bug. And if you can collect some more data, we will all appreciate your input.

---

### Post by markthekdeguy on 2011-02-07
Akonadi is, for me completely pointless. 
It seems most computer OS vendors assume 
we are all office types and want calender, personal information managers,
work management and all kinds of corporate trash built in to the desktop.
i dont. Nepomuk (what a crap name) and Akonadi are the two KDE technologies that should be optional. You can compile KDE not to use this muk (sic) but mst of us will just disable it. they wont really run, and can be turned off more or less. but slimming down any OS seems to be out of style at present, so we have to do a few tiny tweaks when we install.
at least we dont have to put up with Pulseaudio ):P

---

### Post by hainen on 2011-02-08
Some old blogs from an kdepim dev explain akonadi (and nepomuk and strigi)
[http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/](http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/)
and another blog how kmail use nepmuk. [http://thomasmcguire.wordpress.com/2010/01/18/nepomuk-in-kmail-2/](http://thomasmcguire.wordpress.com/2010/01/18/nepomuk-in-kmail-2/)

Most of the stuff is only accurate if you use the kdepim 4.6 beta (the new kdepim was delayed)
I had some problem with the old kdepim bransh. So I have switched to the new bransh (beta realese) and think its work pretty good.

---

### Post by wizard10000 on 2011-02-08
> **markthekdeguy said:**
> Akonadi is, for me completely pointless.

Same here.  I turned off akonadi *and* nepomuk.

---

### Post by inobe on 2011-02-08
it'll be a great application when it's ready and the bugs are worked out.

it just needs further development.

---

### Post by hainen on 2011-02-09
> **inobe said:**
> it'll be a great application when it's ready and the bugs are worked out.

it just needs further development.

+1 
And I think it will make other application better. Its not logical that every application should implement sync sevices and external interfaces and data handling.
And with nepomuk it should be easier to implement good (advanced) search functionality and metadata handling that not freeze the interface, this is somthing most foss software project have a hard time to do alone (I think).

---

### Post by dargaud on 2011-02-09
> it'll be a great application when it's ready and the bugs are worked out.
Which still doesn't answer the question as to what it's for (I'm sorry but both wikipedia and the project's page are completely obscure as to that). How do you use it ? Do I use it without knowing ?

---

### Post by hainen on 2011-02-09
> **dargaud said:**
> Which still doesn't answer the question as to what it's for (I'm sorry but both wikipedia and the project's page are completely obscure as to that). How do you use it ? Do I use it without knowing ?

As I understand it you can think of it as a proxy to pim data. Application use it. You don't use it directly.
A example I tried today is the the google_data plugin to akonadi, it give akonadi compatible software access to google calendars and contacts. 
An another application I use is the event-list plasmoid. It monitor future events from akonadi's data cache.

---

