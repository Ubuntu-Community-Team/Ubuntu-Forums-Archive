---
title: "Enlightenment (E17) issue with libcore1"
date: 2012-10-16
forum: Desktop Environments
---

### Post by jaws222 on 2012-10-16
I recently installed Ubuntu variant Pinguy 12.04 and the Gnome 3 desktop is extremely buggy.  I decided to try Enlightenment E17 and it works perfectly.  The only tweak I needed (wanted) was to add comp-scale, which I added from the following ppa.

deb [http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu](http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu) precise main  deb-src [http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu](http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu) precise main 

After reloading synaptic I installed the following package:  

emodule-comp-scale

I now have 7 broken packages.  It looks like the main issue is with the libecore1 versions. 

Here is the error along with the terminal output.  Any help is greatly appreciated.

E:  /var/cache/apt/archives/libecore1_201210092056-5139~precise1_amd64.deb:  trying to overwrite '/usr/lib/libecore_fb.so.1', which is also in  package libecore-fb1 1.0.0-2.1


Here is the terminal output:

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of emodule-comp-scale:
 emodule-comp-scale depends on libecore1 (>= 201210031402); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing emodule-comp-scale (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedbus1:
 libedbus1 depends on libecore1 (>= 201210031402); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing libedbus1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeeze1:
 libeeze1 depends on libecore1 (>= 201210031402); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing libeeze1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedje-bin:
 libedje-bin depends on libecore1 (>= 201210092056); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing libedje-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libefreet1:
 libefreet1 depends on libecore1 (>= 201210092056); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing libefreet1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeio0:
 libeio0 depends on libecore1 (>= 201210031402); however:
  Version of libecore1 on system is 1.0.0-2.1.
dpkg: error processing libeio0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of e17:
 e17 depends on libecore1 (>= 201210081918); however:
  Version of libecore1 on system is 1.0.0-2.1.
 e17 depends on libedbus1 (>= 201210050638); however:
  Package libedbus1 is not configured yet.
 e17 depends on libeeze1 (>= 201210050647); however:
  Package libeeze1 is not configured yet.
 e17 depends on libefreet1 (>= 201210051209); however:
  Package libefreet1 is not configured yet.
 e17 depends on libeio0 (>= 201210040519); however:
  Package libeio0 is not configured yet.
dpkg: error processing e17 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emodule-comp-scale
 libedbus1
 libeeze1
 libedje-bin
 libefreet1
 libeio0
 e17

---

### Post by Frogs Hair on 2012-10-16
If you add the ppa after the core from the repository E17 will break because the ppa packages are much newer. When I did this I was able to fix the problem from the synaptic package manager. As I remember I removed the software source and removed the E17 packages manually.

---

### Post by jaws222 on 2012-10-16
> **Frogs Hair said:**
> If you add the ppa after the core from the repository E17 will break because the ppa packages are much newer. When I did this I was able to fix the problem from the synaptic package manager. As I remember I removed the software source and removed the E17 packages manually.


Thanks for responding.  I actually just removed emodule-comp-scale from synaptic and all the broken packages went away.  Did you end up removing your old e17 and then download the newest version?  is that what you'd recommend?  And if I do will it break the current configuration?

---

### Post by Frogs Hair on 2012-10-16
I cleaned all E17 packages before adding the ppa which worked very well for me on 11.10 and 12.04. Finding a similar theme to get my GTK3 applications to match the E17 theme was the hard part.:p

---

### Post by jaws222 on 2012-10-16
> **Frogs Hair said:**
> I cleaned all E17 packages before adding the ppa which worked very well for me on 11.10 and 12.04. Finding a similar theme to get my GTK3 applications to match the E17 theme was the hard part.:p


So if I do upgrade I'll lose everything I currently have?  Will I have to reconfigure from scratch?

---

### Post by Frogs Hair on 2012-10-16
12.10 uses Gnome 3.6 and 12.04 uses 3.4. I have been beta testing but will not try E17 again until I know the PPA will work 12.10.

The E17 core packages are in the 12.10 software center but have limitations as you know because you can't add any modules.

---

### Post by jaws222 on 2012-10-16
> **Frogs Hair said:**
> 12.10 uses Gnome 3.6 and 12.04 uses 3.4. I have been beta testing but will not try E17 again until I know the PPA will work 12.10.

The E17 core packages are in the 12.10 software center but have limitations as you know because you can't add any modules.


Well it wasn't as simple as deleting the emodule-comp-scale package because I hosed my e17 when I logged back in.  But I finally did clean it up and get the new version installed and I got it back to where I want it now.  This newer version is really nice, a lot better than the Gnome and I get no screen tearing and a sweeter interface.  Thanks for all of your help.

---

### Post by jaws222 on 2012-10-16
> **Frogs Hair said:**
> 12.10 uses Gnome 3.6 and 12.04 uses 3.4. I have been beta testing but will not try E17 again until I know the PPA will work 12.10.

The E17 core packages are in the 12.10 software center but have limitations as you know because you can't add any modules.


Now enlightenment is crashing everytime on startup.  I may have to downgrade.  THis sucks

---

### Post by jaws222 on 2012-10-16
> **jaws222 said:**
> Now enlightenment is crashing everytime on startup.  I may have to downgrade.  THis sucks


Went back to prior version.  Everything good now!!!

---

