---
title: "telnet remote X display"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Anywhere on 2006-07-26
Hi all,
I know that with ssh I can export a remote display without problem,
but I have to connect to a pc that only has telnet server.
Is there any way to enable x remote display client on ubuntu? (xubuntu..but I think it's the same thing)
thanks in advance!

---

### Post by cantormath on 2006-07-26
> **Anywhere said:**
> Hi all,
I know that with ssh I can export a remote display without problem,
but I have to connect to a pc that only has telnet server.
Is there any way to enable x remote display client on ubuntu? (xubuntu..but I think it's the same thing)
thanks in advance!

if you want to be able to login to an ubuntu box remotely with the X display you can use RDP or vnc. (man vncserver). VNC is probably the easiest way.
RDP is Also good but it often requires more resources.

I would assume the reason you want to go with telnet is because you are behind a firewall.  Hence, you might need to change the ports if you use vnc or rdp.

Here are a few other solutions that I have seen with similar problems on this situation.

[http://www.debian-administration.org/articles/309](http://www.debian-administration.org/articles/309)

just scroll down there are a few.

---

### Post by Anywhere on 2006-07-26
uhmm...
I try to explain the problem better.
I can't install anything on the server side because i've not administrator access.
I don't need all the desktop box but I've only to launch X application (like ghostview (gv)).
I'm connecting from a xubuntu to a red hat enterprise that have only the telnet server (not ssh).
With others linux distro (like mandrake),i haven't any problem to export telnet display.
```

$telnet server.ip
[..login..]
$export DISPLAY=name_of_my_pc:0.0
$gv&

```
if i'm connecting from a mandriva all work's ok
from the xubuntu, response is
```

gv: Unable to open the display.

```
there's is a way to solve this problem?

many thanks :) (and of course sorry for my bad english)

---

### Post by Anywhere on 2006-08-04
any idea? :(

---

### Post by netztier on 2006-08-04
> **Anywhere said:**
> 
```

$telnet server.ip
[..login..]
$export DISPLAY=name_of_my_pc:0.0
$gv&
```


a few things to check:
[LIST]
[*]has $DISPLAY been set successfully? type echo $DISPLAY to verify.
[*]is "name_of_my_pc" known to the remote box, i.e. can it correctly resolve that name to an IP address? if not, specifiy $DISPLAY with your IP address.
[*]will your system accept an incoming X11 connection from this remote system? for a quick-n-dirty test, run "xhost +" to allow from any remote system, later specify only the allowed remote systems.
[*]can the remote box talk to your system on tcp/6000 which is generally used for X11? Are there any firewalls that would prevent this, especially a "personal firewall" on your local system? 
[/LIST]

When you do X11-Forwarding with SSH, all X11 communication is done through the existing SSH connection/tunnel and therefore will pass through any Firewall that has also allowed your ssh-connection.

On the other hand, if you work with "classical" X11, the application (called "X11 client", here: ghostview) on the remote system  will open a separate connection to the display server (called "X11 server") on your local system, mostly on tcp/6000.
Firewalls and their administrators are not always fond of this.

kind regards

Marc


PS: Please go and have a word with the administrator of that remote system. Running a unixoid OS without some kind of ssh seems a strange idea to me.

---

