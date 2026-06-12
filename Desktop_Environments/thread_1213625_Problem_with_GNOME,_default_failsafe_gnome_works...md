---
title: "Problem with GNOME, default failsafe gnome works..."
date: 2009-07-15
forum: Desktop Environments
---

### Post by ferno on 2009-07-15
Hey everyone.

When I turned off my laptop everything was working fine, but when I started up ubuntu again I got an error (I guess when gnome was loading) saying it had to start a failsafe xterm session.

Then it takes me to a login screen, and after I log in I get another error saying the session lasted for less then 10 seconds, and that the ~/xsession-errors file says:

/etc/gdm/Xsesion: Beginning session startup...
/etc/gdm/Xsesion: Executing deafult failed, will try to run x-terminal-emulator. Failed to contact the GConf daemon; exiting.

And I have no idea why this is happening.

Luckily for now, when that login screen comes up, I click on options and select session, and then choose "default failsafe gnome" and everything works fine.

Is there any way I can reset the gnome config or is there anything else I can do so I can boot up normally again?

Thanks.

---

### Post by Mia1990 on 2009-07-15
from the terminal the command to re install the default ubuntu desktop is

sudo apt-get install ubuntu-desktop

---

### Post by ferno on 2009-07-15
that didn't seem to fix anything, any other ideas?

thanks!

---

### Post by julba on 2009-08-18
Hi,

I got the same problem today after a logout/login. It seems to work ok when I start a gnome failsafe session. Did you solve this problem?

I am running jaunty and I install updates (using Update Manager) whenever they appear. I checked to log files /var/log/dpkg.log* and I could not see that any gnome or gconf related packages were installed since the last working login. AFAIK I have not done any changes to the system which could introduce this error but apparently something is messed up.

Johan

---

