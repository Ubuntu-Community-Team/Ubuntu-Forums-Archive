---
title: "My ubuntu died, I'm starting from scratch"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Dave54 on 2006-07-12
Ever since I updated from Breezy to Dapper, it has been one error after another. It seems as time goes on, my system degrades further and further. All this is to be expected on Windows, but not Linux. I generally get errors when I update, install, uninstall, or reinstall anything. Also, my installed software is breaking down. Some programs close unexpectedly, and others don't open. I've actually had my computer completely freeze. At this point I can no longer update my system so I'm going to reformat and install Dapper clean. I decided to copy down the most recent errors in case anyone's interested.

Software index is broken - It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

dpkg: warning - old pre-removal script returned error exit status 102

dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack): subprocess new pre-removal script returned error exit status 102

Errors were encountered while processing: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb - E: Sub-process /usr/bin/dpkg returned an error code (1)

You have 1 broken package on your system! - Use the "Broken" filter to locate it.

The following problems were found on your system: E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102

E: samba: subprocess pre-removal script returned error exit status 102

There were others not related to "samba", but I couldn't get to them before samba made errors. Also at this point it is impossible to install/uninstall/etc anything in synaptic.

---

### Post by Paerez on 2006-07-12
did you try using aptitude to fix packages?

---

