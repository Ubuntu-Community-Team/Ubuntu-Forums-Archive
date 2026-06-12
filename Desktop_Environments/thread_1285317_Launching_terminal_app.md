---
title: "Launching terminal app?"
date: 2009-10-07
forum: Desktop Environments
---

### Post by bhart007 on 2009-10-07
Im trying to create a launcher for the cisco vpn client.. 

path is /etc/init.d/vpnclient_init start -- daemon
and /usr/src/vpnclient connect <profilename>

Except they needs to be ran with a sudo.  I modified the visudo and added lines for: user ALL=NOPASSWD: /usr/src/vpnclient and /etc/init.d/vpnclient_init

But I cant figure out how to get the terminal window to appear...

Help?

thanks

---

### Post by bhart007 on 2009-10-07
wow i think i figured it out.. tried searching here.. no dice.  Search google and it leads me right back here ;p

in the command field in the properties of the launcher..

xterm -e /path/path/executable


AWESOME!!

Oh and gksu for those not needing a term window but requiring su privs.

---

### Post by doas777 on 2009-10-07
I believe that when you create a new launcher, that the second control down says "Application". you shoudl be able to pull it down and select "Application in Terminal" or some such.

---

### Post by bhart007 on 2009-10-08
holy crap.. now I feel stupid.  Thanks for the heads-up!

---

