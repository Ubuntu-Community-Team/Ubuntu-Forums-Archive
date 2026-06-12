---
title: "[Lubuntu]Installing Dock Manager"
date: 2016-11-25
forum: Desktop Environments
---

### Post by notmatt2 on 2016-11-25
Hey Everyone,

Relative noobie here. Sorry if this is in the wrong spot. 

I'm having trouble installing Dock Manager. I downloaded some kind of package from here: [https://launchpad.net/dockmanager](https://launchpad.net/dockmanager)

 I looked at some advice for installing tar.gz files. It says there should be a readme, or an install file, btu I found neither with the package. It also said something about .config, which I couldn't find. Can anyone explain how to install this on Lubuntu for me? I am fairly competent with terminal at this point so hopefully I can follow instructions.

Thanks so much for your time.

---

### Post by deadflowr on 2016-11-25
*Thread moved to **Desktop Environments**.*

You should be able to install dockmanager via docky.
As it is a recommended package for docky, and Ubuntu defaults to installing recommended packages, so
```
sudo apt-get install docky
```
should install docky and dockmanager.

Note as from what I can tell dockmanager has been moved to a virtual package for Ubuntu 16.04.
So while it is still listed as a recommended package for docky, it no longer exists as a real package, but something probably built into another package. Most likely docky itself.

I'd try to ignore the tar file you downloaded, as the page itself tells you that it is no longer supported.
Save yourself the heartaches.

---

### Post by notmatt2 on 2016-11-25
Thanks for the reply. I do have Docky installed, and tried to reinstall it, but I was unable to get dock manager. 

I think I'm going to give up on it for now because I can't even get my wireless working.

---

