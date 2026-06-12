---
title: "Thin Client desktop environment"
date: 2019-06-11
forum: Desktop Environments
---

### Post by webmiester on 2019-06-11
Hi everyone,

I would like my windows machines to be able to access a remote desktop into ubuntu.  But I would like each windows machine to have their own desktops.  It is more like a thin client setup with the windows machines acting as a thin client and the Ubuntu machine acting as a thin client server.

I am reading on xrdp.  Can I have multiple users logging into xrdp at the same time?  Thanks

Thanks

---

### Post by TheFu on 2019-06-11
x2go - [https://wiki.x2go.org/doku.php/doc:installation:start](https://wiki.x2go.org/doku.php/doc:installation:start)

First step is to get ssh working between any Unix client and the Unix server.  Ignore this for Windows clients.

Server install: [https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](https://wiki.x2go.org/doku.php/wiki:repositories:ubuntu)  The x2go server only runs on Linux systems.  On ubuntu, use the PPA for both the client and the server parts.

Client install for Windows - [https://wiki.x2go.org/doku.php/download:start](https://wiki.x2go.org/doku.php/download:start) , get the client install package and the fonts package.  

Desktop connections aren't per client computer, they are per-userid. If you want different clients to have different desktops, then they need to have different userids.  They can connect to the same computer or each to connect to a different computer/VM.  Connections work through the existing (you need to setup) ssh-server process.  Secure it just like you would secure ssh - well, because it is using the main ssh server for connection authentication, any security should have already happened.

If you are doing this for 50+ people, then it would make sense to get a real VDI deployment from someone like Citrix.

x2go feels 2-3x faster than any of the non-commercial solutions. x2go uses the NX protocol which has ssh-tunnels and image compression settings beyond what other F/LOSS solutions have.  The x2go client has a nice GUI and it works from Windows, Linux, BSD and OSX clients.

We've had 6 users connecting to a single x2go server concurrently without performance issues. Never tested more because that was all the people we had.  Since everyone was working together, having some shared storage areas on the machine was useful so they could share files locally.  Performance wasn't a problem, just provide sufficient CPU and RAM for the workload.  It is handy to have groups on the same system for those reasons.
There are good reasons to have separate VMs for each connection too - mainly if they are working on super secret different projects or you need to lock down system networking differently between the VMs, for some reason.  But maintaining more OS installs is a PITA best avoided when possible.

---

