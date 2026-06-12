---
title: "BOINC + Cluster"
date: 2010-04-16
forum: Education &amp; Science
---

### Post by Andy0 on 2010-04-16
Hey everyone,

I want to build a 'cluster' of computers running BOINC. I use the term cluster in the following context: Each computer is a unique copy of an OS (maybe Ubuntu or other) that has its own separate connection to BOINC and determines its own workload. 

I want to use the BOINC system as it was intended. Each computer determines its processing ability, then communicates with projects to get work units. I don't want a central server that grabs BOINC work and then distributes it across the cluster. [eg not this: [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")]

To simplify management I want to update only one computer to update. I want to have a master image or 'server' that is imaged by the 'nodes'. The hardware will be different across the cluster. I think I can use DRBL (Diskless Remote Boot in Linux)[http://drbl.sourceforge.net/]("http://drbl.sourceforge.net/") but I'm not sure. However each node must have its own individual storage area of BOINC storage and configuration. 

To reiterate: I want to build a 'cluster' of individual notes that are all performing BOINC processing, each with it's own individual instance of BOINC.

I think this is the proper way to properly use BOINC while still building a cluster. If you can point me in the right direction that would me amazing!

---

