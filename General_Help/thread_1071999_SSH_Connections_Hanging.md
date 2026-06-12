---
title: "SSH Connections Hanging"
date: 2009-02-16
forum: General Help
---

### Post by bpaulsen1980 on 2009-02-16
I recently setup my first Ubuntu server (8.10) for personal development purposes.  Additionally, I've installed OpenSSH on the machine to allow myself to work directly on the machine via PuTTY and SSH.  At first everything seemed to work great, but recently I've been running into an issue where my SSH connection hangs or freezes at seemingly random points during my work.  Moreover, I've noticed that when this occurs kern.log reports messages such as the following:

```

Feb 16 21:38:49 hornsby kernel: [37335.903335] sshd[30259]: segfault at 1 ip 00000001 sp bf8ed6e5 error 4 in zero (deleted)[b7a84000+140000]
Feb 16 21:38:55 hornsby kernel: [37341.785701] sshd[30261]: segfault at 3b ip 0000003b sp bfe9acc5 error 4 in zero (deleted)[b7931000+140000]
Feb 16 21:39:01 hornsby kernel: [37347.833491] sshd[30263]: segfault at 3b ip 0000003b sp bfe56475 error 4 in zero (deleted)[b79ec000+140000]

```

I've googled essentially every possible combination of the terms in these error messages, but have been unable to find any help to resolving this issue.  Thus, I now turn to this forum in hope that someone can shed some light on the problems I'm experiencing.

A couple of other notes about my environment that may be of use:
* The server is connected to my home router wirelessly.
* I'm running a Squid Proxy Server on the same box and connecting to it via an SSH tunnel and port forwarding on my local machine from 8080 to 3128 on the server.

Again, any information explaining what could be causing my problems would be GREATLY appreciated.

---

### Post by bpaulsen1980 on 2009-02-18
Spent several more hours today attempting to figure out what is causing these sshd segfaults, and I still have no real definitive conclusions.  About the only thing I can say for certain at this point is that the problem appears to be getting worse over time.  When I first setup the box, I had little to no problems with OpenSSH.  Now, I'm lucky if I can even get it to respond on a login attempt.  I would say about one out of five attempts works, and then if I attempt nearly any command the connection hangs and there's a segfault in the kern.log.

A couple of things I've tried so far to no avail:
(1) I ran x86 memtest and there appeared to be no problems with my ram (not sure how reliable this is).
(2) I tried updating and upgrading all of my packages via "apt-get update" and "apt-get upgrade".
(3) I've installed and uninstalled openssh-server as well as openssh-client multiple times.
(4) I disabled IPv6 in sshd_config.

I think it's probably also worth noting that even attempting an SSH from the server to itself is spotty.  So, I guess that's pretty indicative that the problem is with the OpenSSH Server ...

Ugghh!

If anyone has any suggestions on next steps that I can take to resolving this issue, as previously stated, I would GREATLY appreciate it.  At this point, I feel like I'm taking crazy pills...

---

### Post by bpaulsen1980 on 2009-02-18
A little more to add to this ...

Changing the MTU to 576 for both the Ubuntu server's wireless card as well as the router, has seemed to improve stability once I'm connected via SSH.  That said, I'm still having issues just connecting with PuTTY.  About 4 out of 5 times, I get a "connection unexpectedly closed" error message when I try to establish a connection.  This, of course, is also associated with a segault in kern.log.

I suppose I can live at this point, so long as I stop experiencing disconnects mid-connection.  But it would be nice to get this completely stabilized, including the connection initializations.

---

### Post by loy on 2009-03-30
I solved a similar problem with my Ubuntu servers (v8.04) - my ssh connection hanged randomly and only ssh restart helped for a time.

I'm using default UFW and therefore I tried to comment following line in /etc/ufw/before.rules file:
  -A ufw-before-input -m conntrack --ctstate INVALID -j DROP

Bingo! SSH works perfectly now.

My explanation: SSH needs to process invalid packets from unreliable or noised networks (such as wireless). SSH needs to know when to request the new valid packets from the opposite SSH connection side.

Please, try to change your firewall settings and I hope it helps you too.

---

