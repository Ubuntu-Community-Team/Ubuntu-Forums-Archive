---
title: "FreeNX won't connect"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Valeran on 2005-11-01
Hi all!  I've read all the previous posts regarding FreeNX, but I was unable to find a solution to the issue I am experiencing.  So I thought I'd throw my issue out to this great community!  I installed FreeNX on my Ubuntu machine via Synaptic Package Manager.  I added a user to NXserver following the instructions.  I have port 22 forwarded through my router to my machine and I am able to SSH to it from remote locations.  When I attept to connect to my Ubuntu machine from a Windows client using the NOMachine client all goes well until the point when it should display my desktop.  I get authenticated and the keys match with no problems, but the client then just crashes and disappears.  Here is the error message I get from the NOMachine client.

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '3604'.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using wan link parameters 16384/8/5/20.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Using ZLIB data compression level 1.
Info: Using ZLIB data threshold set to 32.
Info: Not using ZLIB stream compression.
Info: Using remote ZLIB data compression level 1.
Info: Not using remote ZLIB stream compression.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

I'm unsure how to get the error messages, if there are any, from my Ubuntu machine.  If someone thinks those would be helpful, please tell me how to get them and I will post it.

Thanks in advance for the help!

---

### Post by Valeran on 2005-11-01
Actually found my own answer.  If anyone needs it follow these instructions.  Works like a charm.

[https://wiki.ubuntu.com/BackportsFreeNX](https://wiki.ubuntu.com/BackportsFreeNX)

---

