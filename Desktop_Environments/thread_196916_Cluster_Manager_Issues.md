---
title: "Cluster Manager Issues"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Aphotic on 2006-06-14
I am relatively new to linux, but I have still piddled aorund enough to know a bit of what I'm doing. (Compiled OS in Gentoo before with LOTS of help from friend over ssh) Recently I was downloadign software when my router froze, so I reset the router and since then my Breezy OS hasn't been able to install software properly, here's the error messages I get from Synaptic:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

Any suggestions? I already tried reinstalling Cman, but since it was via synaptic, it didn't fix the problem.

---

### Post by neekofab on 2006-08-11
it's kinda catch-22. you need a working cluster.conf in /etc/cluster before the install can complete. Try:

1.First Node
apt-get install redhat-cluster-suite system-config-cluster

This Fails (normal) with the following:
Errors were encountered while processing:
   clvm
   redhat-cluster-suite
   system-config-cluster
   E: Sub-process /usr/bin/dpkg returned an error code (1)

export DISPLAY=client_IP:0.0 (on cluster server)
xhost +server_ip (on client workstation)
system-config-cluster (on cluster server in shell with DISPLAY=client...)
  create new
  DLM
  add nodes & save
vi /etc/hosts
  ip   vmserver1
  ip   vmserver2
  ip   vmserver3
reboot
/etc/init.d/clvm stop
apt-get install redhat-cluster-suite
 will complete install now.
2.Remaining Nodes
apt-get install redhat-cluster-suite system-config-cluster
Fails (normal):
  Errors were encountered while processing:
  clvm
  redhat-cluster-suite
  system-config-cluster
  E: Sub-process /usr/bin/dpkg returned an error code (1)
scp [email]root@first_node:/etc/cluster/cluster.conf[/email] . (on client workstation)
scp cluster.conf [email]root@current_node:/etc/cluster/cluster.conf[/email] (on client workstation)
vi /etc/hosts
 vmserver1_ip   vmserver1
 vmserver2_ip   vmserver2
 vmserver3_ip   vmserver3
reboot
/etc/init.d/clvm stop
apt-get install redhat-cluster-suite[INDENT][/INDENT]

---

