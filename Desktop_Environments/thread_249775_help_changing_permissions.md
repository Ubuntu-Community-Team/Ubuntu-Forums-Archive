---
title: "help changing permissions"
date: 2006-09-03
forum: Desktop Environments
---

### Post by guest5 on 2006-09-03
I need help again, but must admit that I did not forsee the immediate foundness and enuthusiasm Kubuntu has brought to me.  If it weren't for consulting, my mind is already thinking about not using $icro$oft ever again.

Score another convert.

The problem I ran into just now is that I cannot change the permissions for the configuration file for privoxy. 

Error:

The document could not be saved, as it was not possible to write to file:///etc/privoxy/config.
Check that you have write access to this file or that enough disk space is available.

Thanks in advance for the anticipated responses.
g5

---

### Post by aysiu on 2006-09-03
> **guest5 said:**
> 
The problem I ran into just now is that I cannot change the permissions for the configuration file for privoxy. Changing permissions or ownership of a system file is a really bad idea. 

> 
Error:

The document could not be saved, as it was not possible to write to file:///etc/privoxy/config.
Check that you have write access to this file or that enough disk space is available.

Thanks in advance for the anticipated responses.
g5 To edit this file properly, paste this command into the terminal: ```
sudo nano -B /etc/privoxy/config
``` Or read this: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by guest5 on 2006-09-03
yes. of course, I wasn't going to leave the permissions changed, I just forgot how to edit that for some odd reason.  Too much info for one day perhaps.  

one more ? please?

Tor did not start, even after checking the start up box in services (kubuntu).

Any thoughts about that would be most helpful.

Thanks again for the fast responce.  You people are GREAT!

---

