---
title: "Lubuntu 18.04 Minimal Install"
date: 2018-05-06
forum: Desktop Environments
---

### Post by West Swan on 2018-05-06
Hello,

I am searching for a list of what apps are not installed when one ticks the new minimal install option for Lubuntu 18.04 but haven't had much luck.

Basically this is at the spot where you can choose all the 3rd party closed source stuff.  There is now an option for a minimal install in addition to the regular install.

I found the Ubuntu list but not the Lubuntu.

Regards,

Paul

---

### Post by howefield on 2018-05-06
Not specific to Lubuntu but here is a list of the removed packages when selecting minimal installation for for Ubuntu.. [http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove](http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove)

I'd expect it to be the same for Lubuntu discounting the packages that aren't part of Lubuntu, but try looking at your /var/log/apt/history.log file, should tell you there what was removed.

---

### Post by West Swan on 2018-05-06
Thank Howefield,

But I think you give me more credit than I deserve :-)

All that gives me is hundreds of lines starting with the following which I have no idea how to interpret:

[B]Start-Date: 2018-04-26  18:20:33
Commandline: apt-get --yes -oDebug::pkgDepCache::AutoInstall=yes --no-install-recommends install linux-generic adduser apt apt-utils base-files base-passwd bash bsdutils busybox-initramfs bzip2 ca-certificates console-setup console-setup-linux coreutils cpio cron dash dbus debconf debconf-i18n debianutils diffutils distro-info-data dmsetup dpkg e2fsprogs eject fdisk file findutils gcc-8-base gir1.2-glib-2.0 gpgv grep gzip    [/B]plus much  much   more

I did notice that this minimal install still includes Abiword and Gnumeric though which is different to the Ubuntu minimal install which removes LibreOffice.

Interesting.  I'll install both Lubuntu options and see them side by side.

Regards,

Paul

---

### Post by West Swan on 2018-05-06
Very interesting :-)

At least with regards to the apps that can be accessed from the start menu (Accessories, Graphics, Internet, Office, Sound and Video, System Tools and Preferences) there is no difference between the standard install and the minimal install.

The exact same apps are in each section.

Regards,

Paul

---

### Post by cruzer001 on 2018-05-06
That is odd.  Maybe you should file a launchpad bug report.

If you want a minimal openbox install take a look at lxde.

[https://packages.ubuntu.com/bionic/lxde](https://packages.ubuntu.com/bionic/lxde)

---

### Post by West Swan on 2018-05-06
It doesn't really bother me.  

I could have stuffed something up (it happens more often these days - getting old sucks) so can anyone else confirm that I am right or wrong?

---

### Post by cruzer001 on 2018-05-06
I would also like to know, so I'm loading it up.

---

### Post by cruzer001 on 2018-05-06
Your right, no difference in packaging.

Time to sniff around in launchpad.

Not hitting on anything

[https://bugs.launchpad.net/~lubuntu-packaging/](https://bugs.launchpad.net/~lubuntu-packaging/)

Only six choices?  How to report a packaging bug?
[ATTACH=CONFIG]279602[/ATTACH]
Anyone

---

### Post by sudodus on 2018-05-06
Try to direct the bug report against the package **lubuntu-desktop**

If it is not correct, someone who knows better will change it and point to the correct package in the bug report

---

### Post by cruzer001 on 2018-05-06
No go, ended up here

[https://bugs.launchpad.net/lubuntu-next/+bug/1769473](https://bugs.launchpad.net/lubuntu-next/+bug/1769473)

Thanks anyhow

---

### Post by cruzer001 on 2018-05-06
Got an answer

[https://bugs.launchpad.net/lubuntu-next/+bug/1769473/comments/10](https://bugs.launchpad.net/lubuntu-next/+bug/1769473/comments/10)

---

### Post by West Swan on 2018-05-06
Thanks Cruzer001,

It is good to know I'm not losing it entirely :-)

Regards,

Paul

---

