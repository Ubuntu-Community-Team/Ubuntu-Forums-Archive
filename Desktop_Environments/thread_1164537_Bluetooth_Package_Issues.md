---
title: "Bluetooth Package Issues"
date: 2009-05-19
forum: Desktop Environments
---

### Post by uv_goth on 2009-05-19
Tried to install [btnx]("http://ubuntuforums.org/showthread.php?p=7309815") earlier but kept getting bluetooth package errors. Can anyone shed any light?

[I]
dpkg: error processing bluez (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluetooth:
bluetooth depends on bluez; however:
Package bluez is not configured yet.
dpkg: error processing bluetooth (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
bluez-utils depends on bluetooth; however:
Package bluetooth is not configured yet.
dpkg: error processing bluez-utils (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
bluez
bluetooth
bluez-utils[/I]

---

