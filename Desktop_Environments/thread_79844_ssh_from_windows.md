---
title: "ssh from windows"
date: 2005-10-20
forum: Desktop Environments
---

### Post by katiad on 2005-10-20
Hi. I'm looking to set up ssh on my ubuntu box so that I can access it remotely from a windows computer elsewhere. I'm on a small home network accessed by a Dlink router, which... may be the problem. I've installed openssh-server, no errors... and I've used the Dlink router's Virtual Server feature to forward port 22 to the ubuntu box. Yet, when I try to ssh in through windows, using putty, I get a message saying that the remote host has closed my connection.

Ideas on where to start?

---

### Post by NewWithoutClue on 2005-10-21
SSH...
Well ssh doesn't accept all connections on one port....it leaves one open then opens a new one upon connection request....so that more than one person can connect ;)...i have d-link aswell and i just used the DMZ option for the computer running ssh.



Regards,
Paul.



EDIT: unless you knew the range of which ssh used...then you should know what to do with that. ^_^

---

### Post by Riverside on 2005-10-21
[QUOTE=NewWithoutClue]SSH...
Well ssh doesn't accept all connections on one port....it leaves one open then opens a new one upon connection request....so that more than one person can connect[/QUOTE]This is technically incorrect.  The SSH daemon listens by default on TCP port 22.  It can also handle multiple incoming connections on that port.  The listening SSH port can be changed by the administrator of the machine on which the SSH daemon resides, or the SSH daemon can be configured to listen on multiple ports, but that is a totally separate issue.

---

### Post by hajk on 2005-10-21
Do you run a firewall, like Firestarter, on your Ubuntu box? If so, it should be set to allow incoming SSH traffic from everyone? a single IP?

---

### Post by NewWithoutClue on 2005-10-21
Woops, i wasn't to sure, but gave it a shot.
when i made a chat i would load a new socket every connection request and accept on the new...leave it to appear as one single port ( most of the time ).

-.-"

Thanks for the info, though.
Paul.

---

### Post by HermanAB on 2005-10-21
BTW, you can debug connection problems like this with telnet:
telnet  1.2.3.4  22

Then the sshd server should answer.

Cheers,

Herman

---

