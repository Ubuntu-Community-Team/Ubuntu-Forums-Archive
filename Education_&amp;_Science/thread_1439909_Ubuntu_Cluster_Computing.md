---
title: "Ubuntu Cluster Computing"
date: 2010-03-26
forum: Education &amp; Science
---

### Post by renomcdonald on 2010-03-26
Okay, so I have searched and scoured the internet for resources and information pertaining to clustering. I don't even know where to begin, I read about the most random of projects and most of which don't apply to me. Some were even years old.

Anyways..... I recently inherited eight IBM eserver 335s to add among my two G4 xservers. I installed ubuntu server 9.10 with the latest KDE. These are headless units that I vnc into.

What my ideal setup would be to have the ability to use all the resources from all the machines used for one program, like a 3D rendering program or video converting software. Or even better yet, a virtual machine that uses all the resources from the cluster to make it seem like one computer.

 I also found [this]("https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") interesting article that I think may pertain to me but if someone could clarify how this utilizes other resources before I attempt installing it. (I have a feeling that the KerrighedCluster would split load by individual processes and would only help in situations like running a video converter WHILE rendering 3D. Two diffrent programs)

Could someone PLEASE shed some light on up-to-date clustering?

---

### Post by renomcdonald on 2010-03-26
and yes I have view [http://ubuntuforums.org/showthread.php?t=1030849](http://ubuntuforums.org/showthread.php?t=1030849), just didn't want my questions to get overcluttered in the active thread XD

---

### Post by lrilling on 2010-03-29
but you should use that thread though. It's the dedicated thread about Kerrighed on Ubuntu.
Anyway, Kerrighed only supports x86-64, so I think that you won't be able to use it on your machines... unless you find resources to port the necessary bits on your architecture?

Louis

---

