---
title: "All of my AWN applets are gone"
date: 2009-03-06
forum: General Help
---

### Post by JMuffin on 2009-03-06
Recently I followed a guide  ([http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html]("http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html")) to add more applets to my AWN manager. After following the steps the installation process quit and I got the following error

```
dpkg: error processing /var/cache/apt/archives/libawn0-bzr_0.3.1.bzr489.3~intrepid_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0-bzr_0.3.1.bzr489.3~intrepid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now when I go into the AWN manager the only applet listed is the Launcher/Task Manager. I get that something failed and I don't get any extra applets, but where did all the applets I had run off to? Any ideas how i should go about getting them back?

---

### Post by JMuffin on 2009-03-06
Managed to fix my own problem, took a lot of adding and removing, and completely removing a number of packages, but AWN is back with all of it's applets.

---

