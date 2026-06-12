---
title: "3-node cluster"
date: 2009-03-03
forum: General Help
---

### Post by muxecoid on 2009-03-03
Hello. I want to build a small cluster for computational purposes. The system processes will be launched through SSH from remote computer, but I'd like to have an option to use GUI for configuration/installation.

I want the cluster to provide an abstraction of "single computer". I want them to have shared file system that functions like single HDD yet uses the physical hard disks of all nodes if needed. I want it to balance processes (threads if possible) between the nodes transparently. Ability to manipulate process priority is also highly desired.

Possibility to expand the cluster up to 10 nodes is also desired.

Ubuntu is probably not the best choice of distro but this forum is very active and features many competent posters.

What software and networking hardware should I use and where is the modern noob-friendly (as little compiling from source and configuration involved as possible) guide?

Thanks in advance.

---

### Post by handy on 2009-03-03
I think your question would be served best in the Server Platforms sub-forum, so I asked the mod's to move your thread there.

We'll see how we go?

---

### Post by ikonia on 2009-03-03
to be honest no cluster is "noob" friendly, clustering is a reasonably complex setup and if you dont set it up correclty (not just on the OS, but the application, the networking, the hardware compatability etc) you're wasting your time and may as well run it on a stand alone PC.


Have a skim read through this [http://en.wikipedia.org/wiki/Beowulf_(computing](http://en.wikipedia.org/wiki/Beowulf_(computing)) for a general over view and pick out the key points to see if you can meet them before wasting time progressing further.

---

### Post by muxecoid on 2009-03-03
Clarification:

The system will be used for polymer simulations in research projects. Currently the code is not threaded and not optimized for anything. It's just several copies of the executable running in parallel with simulation details specified through config file or command line parameters.

Process migration between nodes is not really required as long as the system can select the least loaded node when computationally heavy task is launched.

If shared processes is something too complicated can I just have the 3 computers share the same /home/users

---

### Post by ikonia on 2009-03-05
use network mount (nfs for example) of /home onto all 3 machines from a central point, maybe even look at something like ldap for user managment to make sure users UID/GID's match up, but thats probably overkill, just try to make the UID/GID of the users the same on all systems

---

### Post by muxecoid on 2009-03-05
> **ikonia said:**
> use network mount (nfs for example) of /home onto all 3 machines from a central point, maybe even look at something like ldap for user managment to make sure users UID/GID's match up, but thats probably overkill, just try to make the UID/GID of the users the same on all systems

Can you explain in more detail (aka link)?

I'm ready to invest some time into making the cluster but the time is measured in days, not months. Where should I start? I heard Bio-linux supports easier clustering but I found little documentation on it.

---

