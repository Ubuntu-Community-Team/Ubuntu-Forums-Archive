---
title: "Please help! I'm having an error with compiz installation"
date: 2006-08-23
forum: Desktop Environments
---

### Post by janhenderson on 2006-08-23
I get the following error when I try to install compiz (repositories added, automatixed ubuntu i386, xgl installed already, stuck on this step in the wiki page - installing compiz - with this error) [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

sudo aptitude install compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  cgwd
The following NEW packages will be automatically installed:
  cgwd-themes compiz-plugins
The following NEW packages will be installed:
  cgwd-themes compiz compiz-plugins
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1273kB of archives. After unpacking 4524kB will be used.
The following packages have unmet dependencies:
  cgwd: Depends: libwnck-1 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cgwd [Not Installed]
cgwd-themes [Not Installed]
compiz [Not Installed]

Score is 17

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Setting up compiz-gnome (0.0.13.37-0ubuntu1) ...
Installing gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-gnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compiz-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up compiz-gnome (0.0.13.37-0ubuntu1) ...
Installing gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-gnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compiz-gnome


I can't even do a sudo aptitude remove or purge of cgwd. I get the same error. See, this is what happens when I try to remove cgwd 

sudo aptitude remove cgwd
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up compiz-gnome (0.0.13.37-0ubuntu1) ...
Installing gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-gnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compiz-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up compiz-gnome (0.0.13.37-0ubuntu1) ...
Installing gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-gnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 compiz-gnome

---

### Post by janhenderson on 2006-08-23
Oh nevermind. I got it fixed. I'm not sure how, but uninstalling compiz got it right, after a few attempts it seems. Weird. It's all working now. I have xgl/compiz running.

---

