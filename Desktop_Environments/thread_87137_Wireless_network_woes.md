---
title: "Wireless network woes"
date: 2005-11-07
forum: Desktop Environments
---

### Post by stran on 2005-11-07
Greetings!

Ubuntu has been great thus far. I've run across a few issues, but none more puzzling than this-

I'm running a Dell Inspiron 6000. No trouble getting all the hardware detected and working. I'm using the Intel centrino wireless card (ipw2200), and it works fine for a while, then suddenly- I'm off the network. It's wierd- the lil' network applet shows me recieving data, but not transmit. I can run the net-admin tool, but reactivating the interface is no help- in fact, it times out (probably because it's not transmitting, only receiving). It would appear that my applications "believe" they're transmitting, but the message never hits the airwaves.

Now, if i restart networking (/etc/init.d/networking restart), all is good.... for a while anyway. Also, there's no real pattern in this. It can take 5 min to drop, or 3 hours. I can push a boat-load of data or no data. It's wierd. 

Any ideas?


thanks, 
stran.

---

### Post by mlomker on 2005-11-07
You could look through the logs in /var/log after this occurs to look for clues.  I'd start with kern.log

---

### Post by LexNix on 2005-11-08
Yeah, I'm having the same problems aswell.

---

