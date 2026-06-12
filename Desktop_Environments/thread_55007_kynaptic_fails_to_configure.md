---
title: "kynaptic fails to configure"
date: 2005-08-07
forum: Desktop Environments
---

### Post by coolclassic on 2005-08-07
Just done a update and after some time kynaptic seemed to have froze so I closed down and found that the configuration had failed to finnish. So I did - sudo dpkg --configure -a - and found that I was unable to connect to one resource sight the connection kept failing.
How can I omit this sight so I can complete the configuration.

---

### Post by arjaybe on 2005-08-07
[QUOTE=coolclassic]Just done a update and after some time kynaptic seemed to have froze so I closed down and found that the configuration had failed to finnish. So I did - sudo dpkg --configure -a - and found that I was unable to connect to one resource sight the connection kept failing.
How can I omit this sight so I can complete the configuration.[/QUOTE]

My upgrades often take "some time."  If it's only minutes, be patient.

Control of "resources" is in the text file /etc/apt/sources.list.  Just open a text editor as root - sudo kwrite or kdesu kwrite if you have created a root user - and insert a # in front of the offending line.  Save the file and run update.  (note: this might be doable in kynaptic.  I'm not in Kubuntu and just can't remember Kynaptic's features.)

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 it maybe worth while installing synaptic and use that instead of kynaptic ...

---

### Post by drizek on 2005-08-07
[QUOTE=Gezzer]it maybe worth while installing synaptic and use that instead of kynaptic ...[/QUOTE]
 ya, go with synaptic. much better than kynaptic.

---

