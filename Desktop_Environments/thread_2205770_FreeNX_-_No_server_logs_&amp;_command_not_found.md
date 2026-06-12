---
title: "FreeNX - No server logs &amp; command not found"
date: 2014-02-15
forum: Desktop Environments
---

### Post by tgp1994 on 2014-02-15
Hi everyone,

I'm trying to setup a FreeNX server in the hopes that this will be a fast and functional remote desktop server that I'll be able to log on with. Unfortunately, I've haven't had the change to try it yet!

I've finished setting it up (at least, I think so) on the server, then I installed the NoMachine client on my windows machine. I fire up the client and provide the DSA key and my user to log in with, and I choose the SSH protocol, although the client says that "the command was not found", although my SSH server header shows up in the log.

Now, when I log in /var/log/nxserver.log, it's completely empty. It's owned by an nx user, although it appears that the server daemon is not writing to it, even though I have the logging level set to 5 in the configuration.

Can anyone help me enable logging, and potentially get log in working as well?

---

### Post by tgp1994 on 2014-02-18
Bump, would appreciate some help on this.

---

### Post by tgp1994 on 2014-02-23
Problem solved.

My issues may have been several fold: According to the FreeNX mailing list, password authentication must be enabled in ssh in order for the nx user to create a session. Also, I needed to copy the default dsa private key for nxserver (found in */var/lib/nxserver/home/default_keys*) to my client and use that while logging in. Finally, it turns out that NoMachine's free client at version 4 does not appear to support connecting to FreeNX server. You are better off just using [OpenNX]("http://opennx.net/") to connect instead.

For anyone who would like to see how this was solved specifically, please see the mailing list archive:

[http://mail.kde.org/pipermail/freenx-knx/2014-February/009983.html](http://mail.kde.org/pipermail/freenx-knx/2014-February/009983.html)

---

