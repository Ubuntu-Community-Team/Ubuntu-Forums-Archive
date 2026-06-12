---
title: "Update causes XGL/COMPIZ to fail?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by oxboood on 2006-09-27
I was running fine with my current XGL COMPIZ setup until recently after some uptades, after a restart it doesnt work... has anybody been expereincing problems with recent updates? If thats not the case what do you think I should do?

---

### Post by PCalitrack on 2006-09-27
Yeah, my window borders disappeared after the update. I just gave up on the whole thing.

---

### Post by oxboood on 2006-09-27
Package Manager actually reports two broke packages...

---

### Post by oxboood on 2006-09-27
Alright Im probably talkign to myself here but... everything seems to run a bit slower. And Ive made some ground on whats wrong with the packages... First off I am missing


> compiz: Depends: compiz-core but it is not installed
          Depends: compiz-plugins (>= 0.7) but it is not installed
  compiz-gnome: Depends: compiz (= 0.0.13-0quinn9) but 0.0.13.41-0ubuntu1 is installed

Found that out after running sudo apt get -f install 


However I ran into these errors:

> Setting up compiz-core (0.0.13.38-0ubuntu3) ...
Setting up compiz-gnome (0.0.13.38-0ubuntu3) ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster




---

