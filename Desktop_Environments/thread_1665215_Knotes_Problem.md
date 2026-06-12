---
title: "Knotes Problem"
date: 2011-01-12
forum: Desktop Environments
---

### Post by bobd72 on 2011-01-12
Hello all.
I have recently upgraded a couple of computers from 10.04 to 10.10.  Neither will run Knotes.
I have uninstalned Knotes and attempted to reinstall.
However it refuses to install.  The message I get is:
knotes:
  Depends: libkdepim4 (=4:4.4.6-0ubuntu1) but 4:4.4.8-0ubuntu0.0.1 is to be installed

There seems to be an incomapibility between Knotes and the libkdepim4 version??

I also tried aptitude reinstall libkdepim4 :

sudo aptitude reinstall libkdepim4
The following packages will be REINSTALLED:
  libkdepim4
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the libkdepim4 package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the libkdepim4 package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download


Any suggestions as to what I should do here?

Thanks

---

### Post by ankspo71 on 2011-01-12
Hi,
After a bit of searching I was able to find libkdepim4 4:4.4.8-0ubuntu0.0.1 in the "Lucid Updates" repository.
[http://packages.ubuntu.com/search?keywords=libkdepim4&searchon=names&suite=lucid-updates&section=all](http://packages.ubuntu.com/search?keywords=libkdepim4&searchon=names&suite=lucid-updates&section=all)

Also, Knotes from the Lucid Updates repository says libkdepim4 4:4.4.8-0ubuntu0.0.1 is a requirement.
[http://packages.ubuntu.com/lucid-updates/knotes](http://packages.ubuntu.com/lucid-updates/knotes)

So do you have the 10.04's Lucid Updates repository (or any other Lucid repositories) still enabled after upgrading to 10.10 Maverick? If you do you can disable it/them in Kpackagekit's settings.

Or you can do it manually by editing your sources.list file. Run this command in the terminal:
```
kdesudo kate /etc/apt/sources.list
```
Now comment out any lines that say "lucid" to disable them. You can do this by placing a "#" in the beginning of the line. 

example:
changing this:
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main
to this:
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) lucid main
will disable the repository.

When you are done, save the sources.list file and exit. 

Now update the repositories by typing this in the terminal:
```
sudo apt-get update
```

Now install knotes any way you prefer and see if the problem still happens. I think Knotes will automatically install the correct version of libkdepim4 too, if it isn't installed.

Hope this helps.

---

### Post by micheldell on 2011-01-12
I have a KNotes problem. I use four virtual desktops, one of which is committed KNotes, can appear, when I restart my computer the size and location of all knotes change. Save the contents of the Notes, other proper tiers such as colour, is locked or hidden, is preserved. Resolution and screen size will not change the restart, I only use one monitor.

---

### Post by bobd72 on 2011-01-12
Thanks ankspo71,
One of the lucid entries (backports) had not been changed during the upgrade.  Things are working now.

Also kdepim packages must have been installed/upgraded when running 10.04 (lucid has 4.4.8 packages in it's "updates" repository), while 10.10 (Maverick) still has 4.4.6 packages, so the system couldn't find knotes 4.4.8 in the maverick repos. 

Thanks for the assistance.

---

