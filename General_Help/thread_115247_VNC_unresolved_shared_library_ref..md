---
title: "VNC unresolved shared library ref."
date: 2006-01-10
forum: General Help
---

### Post by ajaym on 2006-01-10
Running Breezy I can't get vncserver to run up. When I try, vncpasswd reports a missing library, libstdc++6.2.2.so.3 (I am away from my machine so that's my best recollection of the exact filename)

I have libstdc6 installed and if I symbolically link that to the library file it wants, then now I get an unresolved entry point reference (unfortunately at this point I can't recollect the exact entry point it can't find, but that may be irrelevant).

I see that libstdc++ is 6.0.5 and can't locate anything obviously newer, after a good deal of spelunking both the net and synaptic's repositories. I've installed every version of gcc going, just in case.

I then tried going to realvnc, downloaded the latest copy from there and installed it but get the exact same problem.

This has got to be a clueless noob kind of error. Any suggestions?.

---

