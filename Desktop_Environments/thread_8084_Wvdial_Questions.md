---
title: "Wvdial Questions"
date: 2004-12-14
forum: Desktop Environments
---

### Post by jodef on 2004-12-14
I have a PCI US Robotics 56k modem that is not detected by Ubuntu's network connection service so I resorted to using wvdial which detected the modem w/out problems. Two little problems though :

1. Is there a way to use wvdial in conjunction with the modem lights applet (my dial up connection sometimes goes dead would be nice to see the traffic and wvdial doesn't seem capable of this)

2. I would like a user to have access to wvdial but do not want to give the user sudo access any simple way to do this w/out compromising security.

Thanks.  :-k

---

### Post by Nikola on 2004-12-14
[QUOTE=jodef]
1. Is there a way to use wvdial in conjunction with the modem lights applet (my dial up connection sometimes goes dead would be nice to see the traffic and wvdial doesn't seem capable of this)
[/QUOTE]

Use gnome-ppp. When connected, it docks to systray and provides same functionality like modem lights.
[www.gnome-ppp.org](www.gnome-ppp.org)

---

### Post by clasqm on 2004-12-14
[QUOTE=jodef]
1. Is there a way to use wvdial in conjunction with the modem lights applet (my dial up connection sometimes goes dead would be nice to see the traffic and wvdial doesn't seem capable of this)
[/QUOTE]

I'm not on my ubuntu box right now, so I'm short on details, but that is exactly what I have - basically I set up wvdial to work from the command line, then went into the applet's preferences (righclick on the applet) and set "dial" to "gksudo wvdial" and "logout" to "gksudo poff.wvdial". 

Works like a charm, and maybe one day I'll figure out how to make wvdial work as a regular user <g> - no, the "add user to DIP group" tip doesn't do it.

Alternatively, install gkrellm - it gives you the same info as the modem lights applet and a whole lot more besides.

---

### Post by jodef on 2004-12-14
Thanks for the quick responses decided to go with clasqm's suggestion worked like a charm. :smile: 

Also solved my second problem thank you.

---

### Post by shangouet on 2005-06-27
Hello, I'm a new Ubuntu user.

(thanks to Wvdial and slamr, I managed to connect to the internet from my thinkpad T40 with an AC'97 internal modem.)

Now, as I have the same 2 problems as jodef, I'm glad to have seen in here the answer to the first one.

But how did you solve the second one (ie. allow a common user to connect without having a sudo access and typing a password) ?

Thanks.

---

### Post by bit-stalker on 2006-07-21
.... Hi.

I am very very new to ubuntu and i am having a hard time installing and external modem / create a dialup connection.

i am actually using a CDMA phone and i normally install a standard 19200kbps modem driver in windows XP.

i managed to create a dialup connection using pppconfig with all the standard setting (the file was saved inside /etc/ppp/peers/)] but how do i use wvdial. 

please help!!!!!!](*,)

---

