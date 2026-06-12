---
title: "Fix: flash no longer installs correctly with flashplugin-nonfree package"
date: 2006-09-19
forum: Desktop Environments
---

### Post by opensensesolutions on 2006-09-19
Have you recently tried to install or upgrade your flash player and it didn't work?  There are workarounds such as using automatix or directly installing from the adobe download, but keeping everything in Ubuntu packages is much nicer.

Last week, Adobe (Macromedia) changed the version of flash available on their server and the Ubuntu flashplugin-nonfree package in the multiverse repository has not been updated.  Because multiverse is not officially supported by Ubuntu, I don't know how long it will be before this is fixed in the Ubuntu repositories.

There is a debian package in the unstable contrib repository, but that didn't work for us either.  We took that package:
[http://packages.debian.org/unstable/web/flashplugin-nonfree](http://packages.debian.org/unstable/web/flashplugin-nonfree)
version 7.0.68.0.1 and modified it slightly to make sure all old plugin links were removed first.

We have put a version 7.0.68.0.2 package in our Groovix respitories.  It can be installed with these two commands:
 wget -O - groovix.com/support/ubuntu/dapper/add_groovix_repos.bash | sudo bash
sudo apt-get install flashplugin-nonfree

and then restart firefox or your other browsers.  

The Groovix respositories are stable and maintained by Open Sense Solutions and only contain material that has no potential legal conflicts in the U.S.  For more info on the Groovix repositories see:
[http://groovix.com/groovix_software.html](http://groovix.com/groovix_software.html)

---

