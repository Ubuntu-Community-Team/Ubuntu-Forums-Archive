---
title: "Administrative Applications won't work via System menu"
date: 2006-08-30
forum: Desktop Environments
---

### Post by ScislaC on 2006-08-30
First off, it's not the "hostname" issue (nor compiz repo issue). ;)

If I try to start any of the Administrative Apps installed in the System menu, it will show "Starting Administrative Application" in the taskbar that will remain there for 10-30 seconds or so and then disappear. It doesn't prompt for password as it should and the application never opens.

However, I can launch any of the administrative apps from a terminal via sudo, but if I try with gksu or gksudo they give the same result as trying through the menu.

I have completely removed and reinstalled gksu thinking that might help, but it didn't make a difference. The bizarre thing is that it used to work and no longer does (note: there was a power outage and I had to manually fsck, but the file that turned up in lost+found wasn't related).

Anyone know where I should look next?

---

### Post by ScislaC on 2006-08-31
I know it's evil, but... bump

---

### Post by fragos on 2006-09-19
the host name in /etc/hostname needs to be in the /etc/hosts file as "127.0.0.1 localhost hostname".  Substitute your hostname in that line.  You may need to "sudo nano" a new file and then overwrite /etc/hosts to make the change.

---

