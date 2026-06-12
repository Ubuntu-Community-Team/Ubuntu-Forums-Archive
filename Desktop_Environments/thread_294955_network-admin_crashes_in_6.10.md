---
title: "network-admin crashes in 6.10"
date: 2006-11-07
forum: Desktop Environments
---

### Post by bonzini on 2006-11-07
Hi folks;

I've posted some questions on this in a previous thread but my understanding of the problem was even more muddled then than it is now, so I'm starting a new thread.

Since installing 6.10 (just after the release announcement) I've had intermittent success with running network-admin.

Currently it is not running; bug-buddy jumps in fairly quickly.  I have run it from the command line and here are the results:

clh@dabuntu:~$ gksu network-admin
(network-admin:12087): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(bug-buddy:12132): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave

** (bug-buddy:12132): WARNING **: Couldn't load icon for Open Folder
clh@dabuntu:~$ 

There is one other post on this topic that was caused by a conflict in the /etc/hosts and /etc/hostname files, but I don't believe this is my problem.

Here is my /etc/hostname file:

clh@dabuntu:~$ cat /etc/hostname
dabuntu
clh@dabuntu:~$

Here is my /etc/hosts file:

clh@dabuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 dabuntu

172.16.1.6      ovid
172.16.1.7      petronius
172.16.1.101    gregory


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
clh@dabuntu:~$ 

Those three lines 172.16.xxx are useful when I use openvpn to tunnel into the work network.  I've tried (just now) commenting them out but the network-admin tool fails the same way.

Thanks!!

---

### Post by bonzini on 2006-11-08
(bump)

Please, folks, any thoughts on this?  This morning I noticed some problems with Nautilus too, can't seem to copy fonts into fonts:/// with similar messages if I try to sudo nautilus.

Thanks!

---

### Post by bonzini on 2006-11-08
Here's an interesting coda.

This morning I tried just a "network-admin" at the shell prompt.

Up it came, just fine (today seems like a good day to administer the network).

While network-admin was running, I noticed that my eth0 connection was enabled.  I seldom use this connection so back in 6.06 days I would disable it.  I did so, apparently effectively... and closed the application.

Then I tried to start it from System > Administration > Networking.

Up it came, just fine.

But!  eth0 was active.  So I disabled it, closed the application, and started it again from System > Administration > Networking.

Up it came, just fine, but eth0 active again.

Hmm.  Could this be just some simple permissions problem or setuid thing or something like that?

Thanks in advance for any ideas!!!

---

### Post by mithion on 2006-12-19
I have the same problem, except that mine doesn't even work through the shell prompt.  I've tried reinstalling the package gnome-system-tools which is responsible for network-admin, and I have have been unsuccessful.  I don't understand why it can't be fixed easily (or why it stopped working in the first place).

---

### Post by montag on 2006-12-24
Same problem here.
It worked fine till yesterday.
Running from the shell with sudo does the job, but it's not a solution... :(

---

### Post by montag on 2006-12-24
Reading again this post recalled me that I've added an host just two days ago. Removing this from /etc/host did the trick, network-admin it's now working again.
The problem is that adding a line to this file via either network-admin or nano makes network-admin fail to start.
Maybe it's a (big) known bug?
I'll further investigate... ;)

---

### Post by montag on 2006-12-24
I think it is this bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936)

---

### Post by yooden on 2007-01-02
Happy New Year!

> **montag said:**
> Reading again this post recalled me that I've added an host just two days ago. Removing this from /etc/host did the trick, network-admin it's now working again.

Thank you, you just made my day. I just started to fool around with Ubuntu (coming from Debian), and a critical component failed on the second day. Now I can at least continue with forcing Enlighenment down Eft's throat.

bye,
Yooden

---

### Post by yooden on 2007-01-02
Hi,

> **montag said:**
> I think it is this bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936)

I googled that page before finding this one, but I can't make heads or tails of it. Is it a bug report? What's the bug's status?

FWIW, I saw the error with or without using the command line.

bye,
Yooden

---

