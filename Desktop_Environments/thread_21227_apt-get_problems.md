---
title: "apt-get problems"
date: 2005-03-21
forum: Desktop Environments
---

### Post by slava on 2005-03-21
hi 
i just installed the hoary preview on mac g3 and everything works well, but several packages failed to install. here is what happens

agoldfish@loki:~$ sudo apt-get install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Settiang up cupsys (1.1.23-1ubuntu11) ...
chmod: cannot access `ipp': No such file or directory
chmod: cannot access `lpd': No such file or directory
chmod: cannot access `parallel': No such file or directory
chmod: cannot access `scsi': No such file or directory
chmod: cannot access `serial': No such file or directory
chmod: cannot access `socket': No such file or directory
chmod: cannot access `usb': No such file or directory
chmod: cannot access `/usr/lib/cups/backend/ipp': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gimpprint:
 cupsys-driver-gimpprint depends on cupsys (>= 1.1.4) | cups (>= 1.1.4); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gimpprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-driver-gimpprint; however:
  Package cupsys-driver-gimpprint is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up libsane (1.0.15-4ubuntu2) ...
dpkg: error processing libsane (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems prevent configuration of sane-utils:
 sane-utils depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing sane-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-imaging-sane:
 python2.4-imaging-sane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing python2.4-imaging-sane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-imaging-sane:
 python-imaging-sane depends on python2.4-imaging-sane; however:
  Package python2.4-imaging-sane is not configured yet.
dpkg: error processing python-imaging-sane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing xsane (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gimpprint
 ubuntu-desktop
 libsane
 sane-utils
 python2.4-imaging-sane
 python-imaging-sane
 xsane
E: Sub-process /usr/bin/dpkg returned an error code (1)




thanks for any ideas
slava

---

### Post by cdhotfire on 2005-03-21
delete cupsys in synaptic then re install it. It should work.

---

### Post by Johan on 2005-03-22
[QUOTE=slava]hi 
i just installed the hoary preview on mac g3 and everything works well, but several packages failed to install. here is what happens

agoldfish@loki:~$ sudo apt-get install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Settiang up cupsys (1.1.23-1ubuntu11) ...
chmod: cannot access `ipp': No such file or directory
chmod: cannot access `lpd': No such file or directory
chmod: cannot access `parallel': No such file or directory
chmod: cannot access `scsi': No such file or directory
chmod: cannot access `serial': No such file or directory
chmod: cannot access `socket': No such file or directory
chmod: cannot access `usb': No such file or directory
chmod: cannot access `/usr/lib/cups/backend/ipp': No such file or directory
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gimpprint:
 cupsys-driver-gimpprint depends on cupsys (>= 1.1.4) | cups (>= 1.1.4); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gimpprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-driver-gimpprint; however:
  Package cupsys-driver-gimpprint is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up libsane (1.0.15-4ubuntu2) ...
dpkg: error processing libsane (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems prevent configuration of sane-utils:
 sane-utils depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing sane-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-imaging-sane:
 python2.4-imaging-sane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing python2.4-imaging-sane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-imaging-sane:
 python-imaging-sane depends on python2.4-imaging-sane; however:
  Package python2.4-imaging-sane is not configured yet.
dpkg: error processing python-imaging-sane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing xsane (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gimpprint
 ubuntu-desktop
 libsane
 sane-utils
 python2.4-imaging-sane
 python-imaging-sane
 xsane
E: Sub-process /usr/bin/dpkg returned an error code (1)




thanks for any ideas
slava[/QUOTE]
 You can also try the dpkg --configure -a command. It will try to configure all packages that are not already configured.

---

### Post by az on 2005-03-22
Have you checked the ubuntu bugzilla for a bug like this?  If there is not, you should report it.

---

