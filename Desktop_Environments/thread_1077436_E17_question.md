---
title: "E17 question"
date: 2009-02-22
forum: Desktop Environments
---

### Post by Rotaj on 2009-02-22
I am using a Hardy variant(made specifically for an Acer Aspire One)with LXDE for the DE. I would like to add E17 to the mix.

Is it just as simple as apt-get install, or is there more to consider?

---

### Post by Tux Aubrey on 2009-02-22
The version of e17 in the Ubuntu repos is many years out of date and is really a slightly updated version of e16.

None of the unofficial builds (eg. Debian experimental) that I'm aware of are straight forward to install on Ubuntu.  Others may have had better results or know of a reliable repo.

That said, you could install e17 easily from source code using [THIS GUIDE]("http://ubuntuforums.org/showthread.php?t=916690")

I have done it on an Acer One and am quite happy with the result.

I also did [THIS HOW TO]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") which adds Rui Pais' other scripts (for e17 maintenance) and some other light-weight apps. 

All this works fine on my Acer One (provided I use WICD, rather than Network Manager - and set up the MADWIFI drivers).  I found that Intrepid has a few problems with e17 (fonts and screen res issues with an attached monitor) but that gnome-settings-daemon fixes these.)

If you use the script or my How-To, you can get support at the CafeLinux forums in my sig.

---

### Post by Rotaj on 2009-02-23
First off, Thank you. I had forgotten about the script/procedure to give a Debian/Ubuntu systems an OZ desktop. Would that also apply to other debian based distros, like sidux or AntiX?

---

### Post by gjoellee on 2009-02-23
Yes it should work fine :p In some distros you might not have the "sudo" in front

---

### Post by celticbhoy on 2009-02-23
I used the tutorial in this thread, and it works fine on my one.

[http://ubuntuforums.org/showthread.php?t=916690&highlight=install+e17](http://ubuntuforums.org/showthread.php?t=916690&highlight=install+e17)

---

### Post by Tux Aubrey on 2009-02-23
> **Rotaj said:**
> First off, Thank you. I had forgotten about the script/procedure to give a Debian/Ubuntu systems an OZ desktop. Would that also apply to other debian based distros, like sidux or AntiX?

The scripts should work fine with those - although the Debian Experimental version would probably also be OK (as they are much closer to being pure Debian than is Ubuntu).

---

