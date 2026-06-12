---
title: "Internet Café"
date: 2009-06-11
forum: General Help
---

### Post by KrisDouglas on 2009-06-11
Hello everyone, not a first time poster, but this is a new account. 
 
I have been doing some extensive research on the forums and google for some information for an Ubuntu internet café
 
To begin with I'm gonna tell you a little about how the system is gonna work:

[LIST]
[*]Server: Dual core 2.4ghz with 3gb RAM running LTSP
[*]Clients are Intel Atom based desktops, diskless... I want these to netboot off the server with PXE
[*]I'd like a fairly user friendly system for the users (both staff and customers) to pay for access to the system for a period of time.
[*]The whole network is gigabit based and the internet will be filtered by the LTSP server.
[/LIST]I would like it to be possible to have a timer for the people who pay to use the machines, and for them to be logged off. Futhermore, i would like any settings saved during that session to be erased when the logoff occours, rather than a reboot.
 
I would like this thread to be a resource for people also thinking of doing such things, as I think it's a great use for Ubuntu. 
 
**Resources:**
[http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by Evontroy on 2009-06-11
> **KrisDouglas said:**
> Hello everyone, not a first time poster, but this is a new account. 
 
I have been doing some extensive research on the forums and google for some information for an Ubuntu internet café
 
To begin with I'm gonna tell you a little about how the system is gonna work:

[LIST]
[*]Server: Dual core 2.4ghz with 3gb RAM running LTSP
[*]Clients are Intel Atom based desktops, diskless... I want these to netboot off the server with PXE
[*]I'd like a fairly user friendly system for the users (both staff and customers) to pay for access to the system for a period of time.
[*]The whole network is gigabit based and the internet will be filtered by the LTSP server.
[/LIST]I would like it to be possible to have a timer for the people who pay to use the machines, and for them to be logged off. Futhermore, i would like any settings saved during that session to be erased when the logoff occours, rather than a reboot.
 
I would like this thread to be a resource for people also thinking of doing such things, as I think it's a great use for Ubuntu. 
 
**Resources:**
[http://www.ltsp.org/](http://www.ltsp.org/)

I'm very new to the Ubuntu world so I would not know where to being to start to answer the series of questions that you have listed. However I'm very interested to know what type of tools if any are available for Ubuntu.

---

### Post by jonabyte on 2009-06-11
I suppose you could run a script when the user logs in to log off after a certain time, may not be the best way to go.

---

### Post by KrisDouglas on 2009-06-11
Hmm, Interesting idea, but I was thinking more of a system that makes it possible for the person on the till to generate a temporary user which will log off automatically after a set time.

---

### Post by shel-hall on 2009-06-11
> **KrisDouglas said:**
> Hmm, Interesting idea, but I was thinking more of a system that makes it possible for the person on the till to generate a temporary user which will log off automatically after a set time.
Between the time we arrived in France and the day the phone company finally got our DSL working, we patronized a local Internet Cafe.

Although they were Windows-based, the business model might be applicable to your situation.  They required everyone to choose a username and password, even transient users, and pre-pay.  You could pay in half-hour increments, I think, but the price per hour went down pretty steeply if you paid for a block of time.  The login software kept track of the time you used and deducted it from your credit balance.

I can't remember the name of the software package they use, but it had a sort of Indian/mystic name; not "Karma" but something like that.  

-Shel

---

### Post by KrisDouglas on 2009-06-11
> **shel-hall said:**
> Between the time we arrived in France and the day the phone company finally got our DSL working, we patronized a local Internet Cafe.

Although they were Windows-based, the business model might be applicable to your situation.  They required everyone to choose a username and password, even transient users, and pre-pay.  You could pay in half-hour increments, I think, but the price per hour went down pretty steeply if you paid for a block of time.  The login software kept track of the time you used and deducted it from your credit balance.

I can't remember the name of the software package they use, but it had a sort of Indian/mystic name; not "Karma" but something like that.  

-Shel

That's very near the sort of thing I would want this system to work as. There are some [very] old projects around that say they do that, but LTSP has changed a LOT since then...

---

