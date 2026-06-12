---
title: "Multi screen over multi machine"
date: 2008-09-08
forum: Desktop Environments
---

### Post by dlublink on 2008-09-08
Hey,

I have three computers. All of which has Ubuntu 8.04. I have two screens on "Computer A ", one screen on computer "b" and one screen on computer "c".

I would like to my desktop expand across the four screens. Is there a way to have Computer A have two virtual screens that are actually screens from B and C and send the image to the other machines?

I don't care about 3d or anything, it's mostly firefox, terminal and other graphically non intensive programs.

Thanks,


David

---

### Post by dlublink on 2008-09-08
I believe the project here will do the work I need : 

[http://dmx.sourceforge.net/](http://dmx.sourceforge.net/)

Using the information here :
[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

I downloaded and installed the RPM from the dmx website, I used fakeroot instead of sudo for the alien conversion.

David

---

### Post by dlublink on 2008-09-08
The RPM on the website was compiled against kernel 2.4, so it is too out of date to run on Ubuntu 8.04.

---

### Post by dlublink on 2008-09-08
It says DMX is integrated with X 

[http://sourceforge.net/projects/dmx](http://sourceforge.net/projects/dmx)

---

### Post by Whiffle on 2008-09-08
Check the ubuntu repos:

[http://packages.ubuntu.com/gutsy/xdmx](http://packages.ubuntu.com/gutsy/xdmx)

---

### Post by dlublink on 2008-09-08
There is no man page for X and I can't find information about how I could do this setup, does anyone know where the documentation for this functionality is?

---

### Post by Whiffle on 2008-09-08
Simple setup:
[http://blogs.unbolt.net/index.php/brinley/2007/09/17/simple_xdmx_setup_with_gdm](http://blogs.unbolt.net/index.php/brinley/2007/09/17/simple_xdmx_setup_with_gdm)

More details, al la IBM:
[http://www.ibm.com/developerworks/linux/library/os-mltihed/index.html](http://www.ibm.com/developerworks/linux/library/os-mltihed/index.html)

---

### Post by dlublink on 2008-09-08
I followed the first tutorial and when I start xdmx it says  "unable to connect to X Server".

I checked with netstat -antp and it is running on the network interface. I tried a simple test to just use the local screen, and it doesn't work.

I am logged into the running X Server using gnome I wonder if this makes a difference.

---

