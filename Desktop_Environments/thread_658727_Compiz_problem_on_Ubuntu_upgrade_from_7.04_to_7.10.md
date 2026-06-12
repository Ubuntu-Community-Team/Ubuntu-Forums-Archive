---
title: "Compiz problem on Ubuntu upgrade from 7.04 to 7.10"
date: 2008-01-04
forum: Desktop Environments
---

### Post by electrifyingsoul007 on 2008-01-04
I had upgraded my Ubuntu from 7.04 to 7.10.Upon upgrading it gave some error of the sort dispalyed below.Now I find their is no compiz-fusion installed and its counterparts.Plz help me as to what I should do ?

Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ryanVickers on 2008-01-05
looks like its more serious than 3D being broken (which is my guess, not *just* compiz fusion ;))

upgrading can do this sometimes... I've never trusted it.
For my advice, I'd say backup and re-install :(... but hold out for somehting else maybe... ;)

---

### Post by shifty2 on 2008-01-05
I would probably try and do a clean install after seeing that error message. If you don't want to though, you could try re-installing those packages that are listed at the end and see if that makes a difference:
```
sudo apt-get install -reinstall acpid
```
and then repeat that for the other packages: acpi-support, powermanagement-interface and ubuntu-desktop.

If that doesn't work you could try running:
```
sudo apt-get -f install
  sudo dpkg --configure -a

```
and see what that turns up. Good luck, but a clean install may be the easiest way forward from here.

---

