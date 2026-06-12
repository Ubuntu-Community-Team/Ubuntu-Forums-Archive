---
title: "Nomachine fullscreen mode - nomachine &quot;freezes&quot; on connection interrupt, no reconnect"
date: 2009-12-31
forum: Desktop Environments
---

### Post by misha680 on 2009-12-31
I am using Ubuntu Hardy Heron Amd64 Desktop edition.

Per dpkg -l I have latest versions of nomachine
ii  nxclient                                   3.4.0-5                                                    NX Client
ii  nxnode                                     3.4.0-6                                                    NX Server Node
ii  nxserver                                   3.4.0-8                                                    NX Server

My problem:
* I connect remotely on a wireless connection
* The wireless connection tends to go down from time to time
* I connect in _full screen_ mode, and this has the unfortunate effect of _freezing_ my session (with no way to terminate) upon disconnect
* The session does _not_ unfreeze upon reconnect of connection
* In fact, if I
killall nxssh
killall -9 nxssh
Try to connect again

I cannot "Resume" the session and must "Terminate"

Any help much appreciated.

Thank you!

Sincerely yours
Misha Koshelev

---

