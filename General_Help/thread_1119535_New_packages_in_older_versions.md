---
title: "New packages in older versions"
date: 2009-04-08
forum: General Help
---

### Post by ufis on 2009-04-08
I am running ubuntu 8.04 LTS 

My problem is that it only runs sun java 1.6.0_07, but I would like to run the latest available java.

I have requested a backport, but the maintainer declined.

So I am left to manually install the latest.
I am not keen to download the latest bin from sun and installing that. Seems that a lot of fiddling needs to be done to get that working.

So I was wondering: Can I go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and look for the java package(s) in the latest release and download and install the .deb

Or would it be better to add the latest release's (jaunty) multiverse repository and install from synaptic?

What would be my best option to get the latest sun java, aside from upgrading to the latest ubuntu or downloading the bin from sun?

---

### Post by dcstar on 2009-04-08
> **ufis said:**
> I am running ubuntu 8.04 LTS 

My problem is that it only runs sun java 1.6.0_07, but I would like to run the latest available java.

I have requested a backport, but the maintainer declined.

So I am left to manually install the latest.
I am not keen to download the latest bin from sun and installing that. Seems that a lot of fiddling needs to be done to get that working.

So I was wondering: Can I go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and look for the java package(s) in the latest release and download and install the .deb

Or would it be better to add the latest release's (jaunty) multiverse repository and install from synaptic?
.......

Most packages have dependencies, if you can satisfy them then you can install the package.

You can download the .deb package and try and install it, it will tell you if it can be done or not.

---

