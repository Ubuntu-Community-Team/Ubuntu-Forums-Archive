---
title: "[SOLVED] Broken packages related to printing"
date: 2008-02-27
forum: Debian
---

### Post by p_quarles on 2008-02-27
Okay, so I got all excited about Hardy alpha 5 and decided to give it a try. The only problems it gave me were extremely minor (I like my Artwiz fonts, darnit), but I found it a little less responsive than Lenny, even after tweaking services and so forth. 

The Lenny reinstallation process had some hiccups, though, and I'm hoping someone can suggest something. I cloned my previous installation by passing a package list file to apt-get via xargs. This went fine until it got to msttcorefonts, at which point it wouldn't accept my attempt to hit the "okay" button in ncurses. So, I escaped the process, rebooted into single-user mode, and ran dpkg --configure -a. 

This worked almost okay, and installed everything I need, but the configuration of the ssl-cert package is hanging. This is, alas, a dependency for CUPS and the HPLIP drivers and interface tools. The exact error messages I'm getting:
```
lee@Rimbaud:~$ sudo apt-get -f install
[sudo] password for lee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ssl-cert (1.0.15) ...
```
It hangs here indefinitely, until I hit ctrl-C. After escaping the process, I get this output:
```
dpkg: error processing ssl-cert (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of cupsys:
 cupsys depends on ssl-cert (>= 1.0.11); however:
  Package ssl-cert is not configured yet.
dpkg: error processing cupsys (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7.10-5); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs-ppds:
 hpijs-ppds depends on hpijs (>= 2.7.10+2.7.10-5); however:
  Package hpijs is not configured yet.
dpkg: error processing hpijs-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing hplip-gui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ssl-cert
 cupsys
 hplip
 hpijs
 hpijs-ppds
 hplip-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This is not an urgent issue at all. I rarely use my printer, and I have other computers to use if I need to. It's also not preventing me from installing any other packages. 

Still, if anyone has any insight into possible fixes, I would be grateful.

---

### Post by jeffus_il on 2008-02-27
Have you tried to install ssl-cert on its own prior to cups? Mine is installed fine in the latest Hardy.

---

### Post by p_quarles on 2008-02-27
> **jeffus_il said:**
> Have you tried to install ssl-cert on its own prior to cups? Mine is installed fine in the latest Hardy.
Yeah, I've tried pretty much every variation on that:
```
apt-get install ssl-cert
dpkg-reconfigure ssl-cert
dpkg --configure ssl-cert
```All of these result in exactly the same output as I posted above. The one thing I haven't tried though, come to think of it, is installing a standalone deb package. I'll go see if that works.

EDIT: D'oh. Nope. Same result using dpkg -i.

---

### Post by jeffus_il on 2008-02-27
Strange, it's virtually a non-package:
> Simple debconf wrapper for openssl 
This is a package to enable unattended installs of software that
need to create ssl certificates.
Basically, it's just a wrapper for openssl req that feeds it the correct
user variables.

---

### Post by p_quarles on 2008-02-27
> **jeffus_il said:**
> Strange, it's virtually a non-package:
Good point, and thanks for the info. That means that either A) the package record for ssl-cert got corrupted; or B) there's a problem with one of the packages on which it depends. 

Too close to my bedtime to do much fiddling right now, but this sounds like a promising direction.

---

### Post by stream303 on 2008-03-01
I ran into the same problem with ssl-cert.  I just removed the package entirely, waited a few days, and tried to bring it back (apt-get install ssl-cert) and the newer version worked fine.  I think I may have even done the same for cupsys.

---

### Post by p_quarles on 2008-03-01
> **stream303 said:**
> I ran into the same problem with ssl-cert.  I just removed the package entirely, waited a few days, and tried to bring it back (apt-get install ssl-cert) and the newer version worked fine.  I think I may have even done the same for cupsys.
Yep. That's what I decided to do as well, and was able to get it installed today. Must have been a problem with the package, and not my installation.

---

