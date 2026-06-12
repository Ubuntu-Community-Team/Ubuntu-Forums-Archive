---
title: "right way to nxfree nx free ubuntu 6.06 rdp"
date: 2006-08-03
forum: Desktop Environments
---

### Post by AllBuntu on 2006-08-03
Hi all,

I got the remote software nxfree running across my boxes, but not the way I want it:

my conclusions
a> nx server is only free on Linux
b> Windows XP Pro can be connected via Gnome > Applications > Internet > Terminal Server Client
c> Windows XP Home uses the SLOW vnc

issues
1) How can I connect through an sshd gateway machine to nx server running on another machine inside the firewall
With ssh I can connect through one machine to another, e.g. come in through port 22, port forward to some Windows port 3389 for rdp. This way no insecure windows is facing the Internet. How do I do the same with nx client and nx server?

1a) If end-machine is Windows, maybe I can not have nx server running for free and it may not be possible?
1b) should I connect using ssh, set up port forwarding and then start nxclient using a port on the local machine that is forwarded?

2) network problems leading to broken connections leaves the session alive on nx server. When nx client is reconnected it is not aware of the previous session and can not connect to it. By using nx sessions on the nx server machine, the old session can be killed but not re-connected to. How can I connect to an old session  that my local nx client is not aware of?

3) Can I use nx client and connect to the existing "console" gnome session? Usually nx client creates its own session and you can either locally vnc into the existing gnome session or kill it - a lot of work and potential data loss. How can I share sessions between being at the machine and remoting to it nx client?

4) Is it true that a nx server for Windows is not available for free?

Thanks to all
Buntu

---

