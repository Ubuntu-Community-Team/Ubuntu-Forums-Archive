---
title: "Port for bittorrent?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by masterjonny on 2006-06-23
Im using the default bittorrent client that comes with Ubuntu and I cant find what port its using, so I dont know what port to foward. Wheres the options menu for this thing so I can set it up? :)

---

### Post by stinerman on 2006-06-23
IIRC, 6881 is the default port.  I don't use the default client, so I'm not sure if it will try 6882-6889 if it can't open the default.

As far as I know, that is hard-coded into the program and it being a minimal client, there is no way to change it.

---

### Post by masterjonny on 2006-06-23
Thanks a lot mate, i'll try those and if not ill move onto something better...just its no fun downloading at 20kb/s on a 8mb pipe >.<

Any reccomendations for a good GUI client? (thats easy to setup)

---

### Post by stinerman on 2006-06-23
When I was on XP, I enjoyed uTorrent.  Apparently it works under wine these days.  Its not F/OSS, though.

I'd prefer Azureus, but I've not been able to get it running with gcj and the sun java implementation is right out for me.  Its also a bit bloated for my needs.  

KTorrent is good if you're using any KDE libs.

I'm using the "mainline" client at bittorrent.com.  For some reason the ubuntu/debian packages stopped at version 3.4.2.  You can download the .deb from the website and install it manually using gdebi or dpkg.  Of course, you have to hunt down the dependencies as well.

---

### Post by theanswriz42 on 2006-06-23
You can use the --minport --maxport switches to give it a range so you can connect to a given port IIRC

---

### Post by JARofHERB on 2006-06-23
Thats true theanswriz42.. 
Also bittornado and the bittornado gui is very nice, you can specify the port range, its super low pro,low memory usage indeed. I always like to use a port from 50000-60000 so that whatever isp/hacker will not really expect that thoes ports are using torrent..

---

### Post by masterjonny on 2006-06-23
> bittornado gui is very nice

Thanks for the help, got a GUI client I can work now :)

---

### Post by virtuethecat on 2006-07-02
[QUOTE=theanswriz42]You can use the --minport --maxport switches to give it a range so you can connect to a given port IIRC[/QUOTE]

hi linux noob here

i'm still getting a hang of things
but as far as changing minport maxport range?

where do i go

if anyone could provide some stepwise instructions

because i wouldn't know where to go to change these values if there's not
a file or preference attached to the program

thanks for the help folks

---

### Post by virtuethecat on 2006-07-02
hey i'm a coffee bean

i feel sophisticated

i think i'm going to have a cigarette and then toil over some unrealized novel idea now

haha, just joking
coffee beans?  great

---

### Post by hoodwink on 2006-07-02
[QUOTE=masterjonny]Thanks a lot mate, i'll try those and if not ill move onto something better...just its no fun downloading at 20kb/s on a 8mb pipe >.<

Any reccomendations for a good GUI client? (thats easy to setup)[/QUOTE]
Install kubuntu-desktop and run Ktorrent. It requires almost no setup.

---

