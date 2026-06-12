---
title: "Proxy question"
date: 2006-07-20
forum: Desktop Environments
---

### Post by evillawngnome on 2006-07-20
SO, i want to set up a personal proxy. Under ubuntu 5, i was basically just VNCing in from work. Now, id like to set it up so that instead of routing video and sound and everything else, im just connecting to the internet through my home computer. Maybe this diagram will help:

Currently, this is how my stuff works here at work:

laptop ---- firewall ---- internet --//-- blocked ports/sites

This is how i get around it:

laptop ---- firewall ---- VNCHomeBox ---- internet ---- blocked sites

This is a waste of bandwidth. Id like to do THIS:

laptop ---- firewall ---- HomeWebProxy ---- internet

I know this is possible. Can anyone point me to a how-to, or give me the names of some tools to research? I would love to write up a how-to on this, particularly for people in countries like india. THey could bounce through a friend here in the states to do their blogging/surfing.

Thanks for listening. :D

---

### Post by kingmonkey on 2006-07-20
I found this website a while back, dont know if its what you need, but might be a starting point.

[http://www.howtoforge.com/book/print/604](http://www.howtoforge.com/book/print/604)

---

### Post by BoyOfDestiny on 2006-07-20
> **evillawngnome said:**
> SO, i want to set up a personal proxy. Under ubuntu 5, i was basically just VNCing in from work. Now, id like to set it up so that instead of routing video and sound and everything else, im just connecting to the internet through my home computer. Maybe this diagram will help:

Currently, this is how my stuff works here at work:

laptop ---- firewall ---- internet --//-- blocked ports/sites

This is how i get around it:

laptop ---- firewall ---- VNCHomeBox ---- internet ---- blocked sites

This is a waste of bandwidth. Id like to do THIS:

laptop ---- firewall ---- HomeWebProxy ---- internet

I know this is possible. Can anyone point me to a how-to, or give me the names of some tools to research? I would love to write up a how-to on this, particularly for people in countries like india. THey could bounce through a friend here in the states to do their blogging/surfing.

Thanks for listening. :D

Hi, I've been playing with ssh on my home network. It sounds like it can do what you need. Install openssh-server on your home box.

Now from your laptop (let's say your username is myname and your ip at home is 67.45.23.101)

from a terminal

ssh -X myname@67.45.23.101

then it's like you are on your machine

firefox

and you are good to go.

The only caveat, is from outside I'd feel uncomfortable being able to log in to a sudo account (even though ssh traffic is encrypted). I will play around with it a bit more, I'd probably just make another user account with limited priviledges and make sure that's the only one that accepts an SSH login.

For your firewall, ssh uses port 22 if I'm not mistaken.

If anyone has a hint or tutorial for setting only one user account to be ssh accesible, please point me to it.

EDIT: Found it

gksudo gedit /etc/ssh/sshd_config

AllowUsers jane john

sudo /etc/init.d/ssh restart

AllowUsers from what I gather are the accounts that are allowed remote login on the host. I will test it out soon. :)

---

### Post by evillawngnome on 2006-07-20
The problem is that my laptop at work here is a windows machine. Ive re-thought things, and my plan right now is to use FreeNX which is a more efficient VNC/RDP type program, and also OpenSSH server. Between the two, i should be able to access anything. :D

THe tutorial im using to install FreeeNX is here:
[http://applications.linux.com/article.pl?sid=06/05/05/1718238&tid=26&tid=47&tid=29](http://applications.linux.com/article.pl?sid=06/05/05/1718238&tid=26&tid=47&tid=29)
I'm going to be doing this RIGHT NOW, so i'll post an update when i'm all done and tell you how it all went.

---

### Post by evillawngnome on 2006-07-20
ABandon'd: Could not get it to work.

After thinking things through, i think VNC is going to be the solution with the most options. Thanks for your help guys.

---

