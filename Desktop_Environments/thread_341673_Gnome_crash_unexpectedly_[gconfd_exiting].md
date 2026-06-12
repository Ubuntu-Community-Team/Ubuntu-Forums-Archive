---
title: "Gnome crash unexpectedly [gconfd exiting]"
date: 2007-01-19
forum: Desktop Environments
---

### Post by daftman on 2007-01-19
Hi,

My gnome desktop freezes unexpectedly.
When I checked my /var/log/messages I found that "gconfd received signal 15" and has shut down.
The odd thing is that after getting into a console (tty1 through ctrl+alt+F1) all the command takes a long time to execute including /etc/init.d/gdm restart. 
I check through my process list but did not see any process hogging up memory or cpu.
Finally I issue a "sudo shutdown -r now" command, the computer takes more than 15 minutes to reboot the system.
Can anyone tell me what else I should have done to diagnose the problem?

I also recall that if I leave the computer running overnight in gnome, this also occurs by the next morning. The crash sometimes would be so severe that I have to manually reboot using the power button. Alt+Sysrec + X was  unrepsonsive

---

