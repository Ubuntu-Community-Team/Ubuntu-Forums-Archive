---
title: "How to temporarily change from dsl to dial up?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by thecdn on 2005-10-31
I live in North Lauderdale,FL and am still dealing with the after affects of Hurricane Wilma. One of those affects is that my dsl has been down for a week and bell south has no idea when it will be back up.

I've been forced to access the internet only through winXP :(   I've gone into network connections and created a dial up connection. 

My question is, how can I do this in Ubuntu? My default connection is obviously dsl and I use both firefox and opera but I don't know how to set up the ubuntu equivalent of the network connections dialup.

Any ideas?

---

### Post by jimbob on 2005-10-31
Open a root terminal and run pppconfig to set your dialup up.

Go into system -> administration -> networking and turn off all active network
devices ( dsl in your case ).

Back in the terminal type pon and it will dial your connection.  

I'm assuming you have a full hardware modem not a winmodem connected.  If it's a winmodem you may have driver problems.

---

### Post by felix_stegerman on 2005-10-31
[QUOTE=jimbob]Back in the terminal type pon and it will dial your connection.[/QUOTE]

And when you're done, you can type poff to disconnect ;-)
You may also want to use the gnome "Modem Monitor" applet.


Felix

---

