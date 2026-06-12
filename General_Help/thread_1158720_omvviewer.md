---
title: "omvviewer:"
date: 2009-05-13
forum: General Help
---

### Post by arizonagirl11 on 2009-05-13
Hi everyone. I am trying to install omvviewer:using the synaptic package manager. in hopes it will clear up my sl problems. Unfortunately, upon attempting to install it, I get the following errors...

The following packages have unresolved dependencies. Make sure that all required repositories are added an enabled in preferences

omvviewer:
 Depends: libboost-program-options1.34.1 but it is not going to be installed
 Depends: libboost-regex1.34.1 but it is not going to be installed
 Depends: libboost-signals1.34.1 but it is not going to be installed
 Depends: libc-ares2  but it is not installable
  Depends: libc6 (>=2.8~20080505) but 2.7-10ubuntu4 is to be installed
 Depends: libcurl3-cares but it is not going to be installed
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
 Depends: libopenal1 (>=1:1.3.253) but it is not installable
 Depends: libopenjpeg2  but it is not installable
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed



any ideas on how to fix this, I would be very grateful. Thanks!

--Kimberly

---

### Post by KhurramM on 2009-05-14
Goto

System > Administration > Software Sources

Select all the sources to yes.

Hope this helps u.

---

### Post by arizonagirl11 on 2009-05-15
I can't get it to work. Thank you though :( I did what you suggested, but I am still getting the same results.

---

### Post by arizonagirl11 on 2009-05-15
I found a web site about downloading omvviewer. the web site is here...

[http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/](http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/)

However, when I attempt to follow the directions, this is what I get when it comes to errors....

Fetched 308B in 16s (18B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97
W: Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.


Does anyone have any ideas about this?

---

### Post by afrodeity on 2009-11-12
Try 

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY
```

Replace KEY with the Key-String, ie 0E931CE221789C97

---

### Post by afrodeity on 2009-12-08
Try Hippo OpenSim Viewer [http://mjm-labs.com/viewer/](http://mjm-labs.com/viewer/)

---

### Post by ell02 on 2009-12-08
Hope you are doing better by now,as this is an old post.Iv'e had good luck with emerald viewer. 

[http://modularsystems.sl/](http://modularsystems.sl/)

---

### Post by afrodeity on 2009-12-08
I checked out Emerald Viewer, its basically the same Second Life viewer which is now available. Hippo has a button where you can change the grids that you log into. Very cool.

---

