---
title: "Swiftweasel slow due to XGL in Gutsy"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by ram100987 on 2007-10-21
It looks that Gutsy is finally working on my Fiances laptop.  it has been running Fiesty and when I upgraded to Gutsy I left it alone to let it do its thing but my Fiance unplugged the laptop without my knowledge so right in the middle of the installation the battery ran out of juice and the laptop turned off.  So even though Gutsy boot up, there was a lot of issues and things missing.  From a tip from another post I tried to uninstall tzdata and reinstall it.  That did not actually work but it did cause it to finish installing a huge list of partially installed things. Once that finished I rebooted, but now it wouldn't even boot up, it kept throwing a kernel panic.  I was able to boot up just fine with the old kernel and after doing some looking around, I found an issue in the menu.lst file.  A very important line was missing from the new kernels boot up options.  so I am now running Gutsy with no apparent issues except one.

whenever I open swiftweasel it runs very slow and scrolling is very laggy and jerky.  I know this is due to xgl because when I ran fiesty, whenever I would boot into an xgl session it would do the same thing, but would work fine in a normal gnome session.  Since Gutsy starts an xgl session by default I don't know how to turn it off.  This is a low end laptop with a SIS graphics card, so I know it can't handle any desktop effects so is there a way I can start up gnome with OUT xgl so that swiftweasel will run properly?

---

### Post by ram100987 on 2007-10-21
After doing some more searching in the forums, I tried uninstalling xserver-xgl but came up with

```
ryan@ubuntu:~$ sudo apt-get remove xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libclan2c2a-jpeg libclan2c2a-sound libswfdec0.3 libclanlib2c2a
  libjack0.100.0-0 libclan2c2a-vorbis libclan2c2a-gui libclan2c2a-png
  libglitz1 libdb3 libclan2c2a-mikmod hermes1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
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
ryan@ubuntu:~$ 

```

Aparently xgl isnt install but it looks like there are some other issues in there.  4 not fully install and acpid won't seem to work....

---

### Post by ram100987 on 2007-10-21
I did the autoremove to get rid of the ones it said were not needed, and after rebooting I am now scrolling normally. :)  But I am still worried about y acpid is not working.  I know it will come back to haunt me later on after I have forgotten all about it.

---

