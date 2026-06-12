---
title: "Looking Glass Desktop Installation"
date: 2008-08-14
forum: Desktop Environments
---

### Post by pikabuntu on 2008-08-14
I get this when I try to install the looking glass desktop environment
does this mean that xorg is missing? if so, what can I do?


zach@zach-desktop:~$ sudo apt-get install lg3d-core
[sudo] password for zach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
zach@zach-desktop:~$

---

### Post by pikabuntu on 2008-08-14
also, this is causing big trouble, because It makes me agree to the looking glass license every time i apt-get something :(  I think that it is trying to install looking glass every time

---

### Post by pikabuntu on 2008-08-14
[http://www.ubuntugeek.com/install-sun-looking-glass-desktop-environment-in-ubuntu.html](http://www.ubuntugeek.com/install-sun-looking-glass-desktop-environment-in-ubuntu.html)

This is where i got the instructions, in case that helps ...

---

### Post by kcode on 2008-08-14
hey,
sorry to pop in.
went to the refered link, and made appropriate changes. on apt-get update got this error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by rodrigth on 2008-10-15
kcode,
this message

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

means that you have something else that manages packages working. this could be another terminal running apt-get or possibly you have synaptic open.

Pika,
The file in the repositories does not work on new ubuntu versions (feisty, hardy)
1. download this file:
[https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb](https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb)

2. then, open synaptic up, and goto settings > repositories and add these (each sepearate) under the third-party tab:
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

3. search synaptic for lg3d, and install ONLY lg3d-jdk and lg3d-java3d

4. once these are done, install the lg3d-core package you downloaded

If all goes well, you should have a running copy of lg3d!

hope this helps guys!
tharon

---

### Post by rodrigth on 2008-10-15
also, check this page out after! lets you know how to control the desktop!

[http://wiki.java.net/bin/view/Javadesktop/FirstRun](http://wiki.java.net/bin/view/Javadesktop/FirstRun)

---

### Post by motogp on 2008-12-05
thank you rodrigth , your instructions did it for me ...
running lg3d on ubuntu 8.10

---

### Post by ninjaaron on 2008-12-20
lg3d-core_1.0.1_dev_i686.deb doesn't work on my amd64 system. Is there any way to get looking glass to work for me?

*edit*
After snooping around the project pages, I'm thinking not.

---

### Post by gw7714 on 2009-02-19
I have done the same thing pikabuntu did, did it all correctly and got the same thing (ERROR 1).  But, just for the heck of it, I tried loggin out and then changing my session type, the error dialog told me to see the "Looking Glass Dveloper's Guide" to get more info on how to build Looking Glass with x11 support. It looked complicated (especially since I am pretty new to linux).So I found this post and downloadded the package you suggested, but could not find the to packages you also said to install when I did the search in Synaptic.  

Should I try to uninstall all the other ones? 

please help!!

thanks!

---

### Post by blackrockzig on 2009-02-19
zach@zach-laptop:~$ sudo apt-get install lg3d-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0+rc1) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)




How do I run the program??

---

### Post by gw7714 on 2009-02-20
I ran the update manager and there is an update for Looking Glass... maybe this will fix it, I'm downloading it right now.

---

### Post by gw7714 on 2009-02-20
I ran the update amnager and there is an update for Looking Glass... maybe this will fix it, Im downloading it now.

---

### Post by gw7714 on 2009-02-20
It installed the update. No luck. Same thing.

---

### Post by Twitch6000 on 2009-02-20
Okay I will tell you how to fix the error,but I can't seem to get it installed myself so... I can't help with that lol...

type this in the terminal -

```
sudo apt-get -f remove lg3d-core
```
If I get looking glass installed I will make a how to lol.

---

### Post by gw7714 on 2009-02-20
a how to would actually be really sweet!

I tried this method, same results though:

[http://www.netdip.com/installing-looking-glass-on-ubuntu/](http://www.netdip.com/installing-looking-glass-on-ubuntu/)

---

### Post by dlatrell on 2009-06-21
I see you give good help.  My issue is I've added the three repositories and my search comes back with failures on all three after selecting reload.  I do have lg3d-core, lg3d-jdk and lg3d-java3d already on my system but I can not get this thing to come up.  I am downloading lg3d coe 1.0.1 dev i686.deb now and I hope that work but it look like the same file that is already installed.  If you suggest or need a readout just tell me and it's done.  Hope you can help

:)


> **rodrigth said:**
> kcode,
this message

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

means that you have something else that manages packages working. this could be another terminal running apt-get or possibly you have synaptic open.

Pika,
The file in the repositories does not work on new ubuntu versions (feisty, hardy)
1. download this file:
[https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb](https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb)

2. then, open synaptic up, and goto settings > repositories and add these (each sepearate) under the third-party tab:
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

3. search synaptic for lg3d, and install ONLY lg3d-jdk and lg3d-java3d

4. once these are done, install the lg3d-core package you downloaded

If all goes well, you should have a running copy of lg3d!

hope this helps guys!
tharon

---

