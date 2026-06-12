---
title: "Error with Gaim"
date: 2005-03-27
forum: Desktop Environments
---

### Post by microo on 2005-03-27
Hi everyone ! I have a problem with this is what i have after an update.

Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gaim-dev:
 gaim-dev depends on gaim (= 1:1.1.2-3ubuntu1-4.10ubp1); however:
  Package gaim is not configured yet.
dpkg: error processing gaim-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim
 gaim-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone help me with that 

Many thanks

Microo

---

### Post by Trab on 2005-03-27
[QUOTE=microo]Hi everyone ! I have a problem with this is what i have after an update.

Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gaim-dev:
 gaim-dev depends on gaim (= 1:1.1.2-3ubuntu1-4.10ubp1); however:
  Package gaim is not configured yet.
dpkg: error processing gaim-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim
 gaim-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone help me with that 

Many thanks

Microo[/QUOTE]
 did u use synaptic/apt-get for this? if u update gaim via dpkg it doesnt really work well... cause its missing dependencies.... as lame as it is, i only update gaim via synaptic, cause better outdated and working than updated and not... :-) good luck

---

### Post by microo on 2005-03-28
I've update vias Synaptic and this is what it gave me.

I have always this message when i install another program from Synaptic.


Need help to get rid of it 


Microo

---

### Post by rkn on 2005-03-28
** sudo apt-get -f install**

(the "f" is for "fix")
will remove the half-installed gaim.  Then you can start over or whatever....


Bob

---

### Post by iomicifikko on 2005-03-29
[QUOTE=rkn]** sudo apt-get -f install**

(the "f" is for "fix")
will remove the half-installed gaim.  Then you can start over or whatever....


Bob[/QUOTE]
 i have that problem too.

its a problem of backports repository. they will fix it. anyway my gaim does its job.
to go back to the earlier installation of gaim using synaptic, just unselect for a while the backports repositories, and update (or simply search gaim)

byez

---

### Post by microo on 2005-03-29
Thank you rkn and iomicifikko i've finally fix my problem.

          =D>  =D>

---

