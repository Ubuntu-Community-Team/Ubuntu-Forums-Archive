---
title: "Ctrl+C on ssh kills local x-server"
date: 2015-02-20
forum: Desktop Environments
---

### Post by mattia.tamellini on 2015-02-20
Hello everybody!

I was not sure where to post this, so bear with me if I chose the wrong section.

I am working remotely with a C++ library (this one: [http://fenicsproject.org/](http://fenicsproject.org/)) via ssh on the computers in the cluster of my university. The ssh connection is established with the flags -CY, so that I can have the remote computer plot the result (using VTK). 
It sometimes happens that when I try to kill a job I launched on one of the computers in the cluster using Ctlr-C my screen goes black for a second and the **local** computer I'm using to connect to the cluster logs off. This behaviour is apparently random, but happens only if a ssh graphic connection is established (or at least it has never happened when I use plain ssh) and it happens only when I'm using the library I linked above.
I tried googling, but I found nothing (perhaps I am using the wrong keywords).

I would attach a log file to this post, but I have no idea where to look for the proper log file, since I cannot wrap my mind around the fact that a **remote** error could kill x-server on my **local **machine.

Does anybody know what's going on? How can I solve this?

Thanks a lot!

---

