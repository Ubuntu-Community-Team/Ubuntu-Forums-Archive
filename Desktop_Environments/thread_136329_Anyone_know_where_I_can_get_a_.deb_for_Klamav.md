---
title: "Anyone know where I can get a .deb for Klamav?"
date: 2006-02-25
forum: Desktop Environments
---

### Post by sweeney276 on 2006-02-25
I've recently been using MEPIS and Klamav was installed by default.  Its a VERY nice KDE GUI to clam antivirus.

I can't seem to find Klamav in the repositories, so anyone know where I can find a .deb for it?

---

### Post by aysiu on 2006-02-25
Enable extra repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then: ```
sudo apt-get update
sudo apt-get install clamav
```

---

### Post by Jucato on 2006-02-25
i think he's looking for KlamAV, the KDE front-end for clamav?

---

### Post by msak007 on 2006-02-26
According to [this]("http://packages.ubuntu.com/dapper/kde/klamav"), KlamAV is in the Dapper repositories. I haven't opened them up so I can't tell you if it'll install if you include them in your sources. I've attempted to install KlamAV manually without any success, so if anybody has a how-to I'd like to see it. I've tried both compiling from source as well as running the installer, but both error out when trying to insert the "dazuko" module. The syntax is incorrect and it errors out. Unfortunately, dazuko is required for KlamAV so it won't install without it.

---

### Post by sweeney276 on 2006-02-26
Yes, I'm after the KDE front end for clamav called Klamav.

I'm surprised that clamav is in the Breezy repositories, but Klamav isn't as yet.  I've tried downloading Klamav from the MEPIS repositories but it must be compiled a bit differently, as it doesn't run under Kubuntu (great under MEPIS, but not good under Kubuntu).  I've tried compiling the tarball, but it doesn't seem to want to compile either.  I might go back and report the problems I've having if others are having the same problems.

Klamav is really nice: it looks similar to ClamWin, which is clam antivirus for Windows.  It enables a variety of tasks to run concurrently with a tabbed interface.

Well, if anyone knows where I can get a .deb that works under Breezy.....

---

### Post by sweeney276 on 2006-02-26
Finally found a .deb for Kubuntu but it's a Dapper app and needs so many dependencies to be updated/installed that I think I'll wait.

Just for info I attach a screenshot of the SimplyMEPIS 3.4-3 live distro desktop, showing Klamav.  Even on the live distro, it allocates space to quarantine and will download the latest virus database.

---

