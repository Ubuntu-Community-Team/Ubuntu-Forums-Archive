---
title: "Using alternate shutdown and reboot commands?"
date: 2009-03-29
forum: Desktop Environments
---

### Post by J@n on 2009-03-29
Hi,

I am experiencing problems with shutdown and reboot from Xubuntu. When I try to shutdown the machine or reboot it, it "hangs". If I disable the splash screen (to see what happens), I get a log-in on the command line of TTY1 but it is not responsive. If I activate TTY7 I can see a message stating:

> All processes ended within 2 seconds

I can wait for as long as I like but nothing happens after that.

If I open a root terminal and issue the command ```
halt -f -p
``` the systems turns off without hesitation. If I issue ```
reboot -f now
``` the systems reboots as expected.

So I decided to change the commands in the GUI (Applications > Settings > Login Window) and clicked "Edit Commands". There I changed the default command for reboot in ```
reboot -f now
``` and did a similar change for shutdown. It did not work:(

Then I changed the commands using the configuration files:
[LIST=1]
[*] /etc/gdm/gdm.conf-custom
[*] /etc/gdm-cdd.conf
[*] /etc/gdm/gdm.conf
[/LIST]

Of course I made one change at a time and tested it. But even after I had changed all files I could not get the system to shutdown or reboot through GDM

So my question is:

Where or how do I change the commands for shutdown and reboot in order for GDM to do its job?

PS. The originating problem is caused by NFS/Portmap but I can't find a solution for it. I must have searched and tried for over a week ](*,)

Any help greatly appreciated!

Greetz,

J@n

---

### Post by J@n on 2009-04-04
No one :confused:

I hoped it would not be too difficult for a real Ubuntu Guru ;)

---

### Post by J@n on 2009-04-26
Well. My first unanswered and therefore unresolved thread.

_CLOSED_

J@n

---

