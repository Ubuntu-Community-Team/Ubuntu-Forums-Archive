---
title: "old problem and still is ....[no wifi ]"
date: 2009-02-15
forum: General Help
---

### Post by madhavhmk on 2009-02-15
there are no drivers listed in system>adminstration>hardware driver

I tried to install the b43-fcutter
the flwing error occured
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

it is so irritating to have to be plugged in with the ethernet every single time.....

there is ndswrapper thing even that is not showing any thing.....pls help



The following NEW packages will be installed:
b43-fwcutter
0 packages upgraded, 1 newly installed, 0 to remove and 178 not upgraded.
Need to get 0B/15.8kB of archives. After unpacking 102kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 160156 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing b43-fwcutter (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up b43-fwcutter (1:011-1) ...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing b43-fwcutter (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
b43-fwcutter
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by fragos on 2009-02-15
Do you actually have a proxy server for Internet Access, 8080 is the normal port for that? Assuming that this is the correct driver for your Broadcom WiFi chip my question would be why has the install process decided you have a proxy? Run "lspci" and post the WiFi chip set it reports. My last laptop I purchased with an Intel WiFi chipset so my install is automatic. In the past I've gotten Broadcom WiFi to work for friends with ndiswrapper and a Windows DLL driver with a different name. I do seem to recall blacklisting the driver that came with Ubuntu. My memory is a bit fuzzy on the subject but do recakk that doing a forum search with the chipset number led me to a solution.

---

