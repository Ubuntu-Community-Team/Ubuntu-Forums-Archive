---
title: "Username at the Console Window"
date: 2006-06-21
forum: Desktop Environments
---

### Post by utab on 2006-06-21
Dear all,

How can I see my username in the console caption.

I know that by changing COMMAMD_PROMPT env variable I may configure that.

This problem started after I have added some lines to /etc/rc5.d/S20samba  to automount some network folders to my system.

Now I can see all the network files I want but the problem is that I can not see the 

username@host 

info on the console window caption. (BTW I can see it on the command line it is true but that must be the same as the command line version on the window caption as well but the username is not displayed, just @host is displayed)

Regards.

---

### Post by lamego on 2006-06-21
You should **not** add mounting commands /etc/rc5.d/S20samba, that is not the purpose of samba startup command. 
During upgrades and because this file is part of the samba package your changes there may be lost.
You should add samba mount points on /etc/fstab .

---

### Post by utab on 2006-06-21
[QUOTE=lamego]You should **not** add mounting commands /etc/rc5.d/S20samba,

Dont worry that is true for my purposes if I make upgrades I know what to do. My real question was not this one, it is related to bash. 

Regards

---

