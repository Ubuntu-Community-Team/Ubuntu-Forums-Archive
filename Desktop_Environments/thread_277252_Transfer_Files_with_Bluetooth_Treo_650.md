---
title: "Transfer Files with Bluetooth Treo 650"
date: 2006-10-14
forum: Desktop Environments
---

### Post by padan on 2006-10-14
I sync all the information I need on my treo from an exchange server, so I really do not need to sync any of this information with my PCs.  However, I would like to be able to install apps and move files from the PC to the treo.  In the spirit of wireless I would love to do this just using bluetooth, which my laptop has built-in.

I have been reading other forum threads and I know that my bluetooth is working and I can get some basic communication going between my treo and the PC.  On the treo, if I go to hotsync, setup devices, I can search for and find my laptop.  Then when I connect to it I am prompted for the PIN that I specified in /etc/bluetooth/pin and it seems to work properly (at least no error messages are displayed).

I have been poking around in some of the sync apps (jpilot, multisync) and I can't see where I can tell it to use the bluetooth connection.  I am assuming that I need to create some device node and then tell the program where it is, however I have no idea where this device needs to point to.  Can someone point me to some documentation?

---

### Post by padan on 2006-10-14
I ended up finding this great howto:
[http://howto.pilot-link.org/bluesync/index.html](http://howto.pilot-link.org/bluesync/index.html)

And I was able to get the network part all setup just fine and now I am here:
[http://howto.pilot-link.org/bluesync/gb.html](http://howto.pilot-link.org/bluesync/gb.html)

In that first picture where it says select 'modem' and then the connection that was created in the previous step, the only connection I can select under the modem is 'MediaNET'.  Any clues as to how I make my 'unix' connection automagically appear?

---

### Post by psycho78 on 2006-11-04
hmm I too can only select virtual modem or standard modem under modem... probably the turorial was made for another firmware of the treo?

---

### Post by psycho78 on 2006-11-04
i found a way to select the right connection under modem, read this article...:
[http://www.linuxjournal.com/article/8185](http://www.linuxjournal.com/article/8185)

I am one step closer to sync but still cannot sync....

---

### Post by psycho78 on 2006-11-04
I finally can sync my Treo650 via Bluetooth...with evolution! :)
But I still can not surf the web using the palm.... it connects to my laptop, ipforwarding is enabled, i have no firewall turned on... hmmmm i think i have to sleep over this, it is 3am already... :(

---

