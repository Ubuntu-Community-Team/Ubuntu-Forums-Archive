---
title: "root terminal &amp; Synaptic stopped working"
date: 2005-10-11
forum: Desktop Environments
---

### Post by barry_s on 2005-10-11
Hi,

I'm a newcomer to Linux, installed Ubuntu last week and I'm now 95% of the way to being MS free (yay!). 

But I've hit one little problem today. I booted up my Ubuntu install, no problem, but if I select Root Terminal from the Applications menu, I get a message at the bottom of the screen which says "Starting Root Terminal", but after a little while it just dissapears and the terminal does not open. Similarly when I select Synaptic from the System menu it doesn't start. Also the notification icon at the top of the screen is red and says there is one update, but if I click on it nothing happens. I figure that these things are probabaly all related, but I have no idea how to fix it :( 

I can open a regular terminal, su to root and open Synaptic that way. Likewise apt-get also works fine that way. 

I realise that these problems don't stop me getting things done, but what I like about Ubuntu (especially compared to Red Hat 6 which was the last time I tried using Linux) is that everything just works!

I'd really appreciate any help anyone can offer.

Thanks

Barry

---

### Post by KingBahamut on 2005-10-11
Sounds like a problem with the actual entries in the menu. 

install smeg and see if you can edit the entries or recreate them proper. 

apt-get install smeg

---

### Post by barry_s on 2005-10-11
Thanks for the advice. I've used Smeg to look at the menu entries, and for the Root Terminal the command is;

gksudo /usr/bin/x-terminal-emulator

if I su to root in a terminal window and type in;

/usr/bin/x-terminal-emulator

the root terminal opens no problem. However if I open a terminal as a normal user and put in;

gksudo /usr/bin/x-terminal-emulator

the result I get is

sudo: /var/run/s

I don't know what that's telling me.

I don't sem to be able to edit the System menu using Smeg, so I don't know what command it is trying to execute. 

Thanks

Barry

---

### Post by barry_s on 2005-10-11
Ooh, I think I've found something. :) If I change the command from;

gksudo /usr/bin/x-terminal-emulator

to

gksu /usr/bin/x-terminal-emulator

it works as it did before. Could this be because I previously used;

"sudo passwd root" so that i could use su root in the more usual way?

If I've done the right thing, I'd be grateful if someone could tell me how I edit the "System" menu either with Smeg or by hand. As this affected the update icon as well I'm assuming I would need to do something about configuring that as well, and again I would be grateful for a pointer in the right direction.

Thanks

Barry

---

