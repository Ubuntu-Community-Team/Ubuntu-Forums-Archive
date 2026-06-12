---
title: "Latitude Ambient Light Sensor - make it working"
date: 2007-07-23
forum: Dell  Ubuntu Support
---

### Post by mikeos on 2007-07-23
With the default Ubuntu installation (tested with Gutsy and Feisty on Latitude D820) the laptop's ambient light sensor (automatic LCD brightness adjustement) does not work. However it's very easy to make it working. Besides that the libsmbios package allows you to update your Latitude BIOS and  get some more information about your laptop via command-line. 

Suppose you have this option activated in BIOS setup. If not, let's do it. 

To activate the software support, first get and install the following package:

```
sudo apt-get install libsmbios-bin

``` 

Make the module dcdbas load automatically with your system start-up. We add the module at the end of the file *modules*.

```
sudo echo dcdbas >> /etc/modules
```

Reboot your system and you're done.

Besides ambient light sensor (which you activate by Fn+Arrow Left) you can use all the variety of Dell utilities, such as retrieval of asset tag, service tag and BIOS update through command-line tools directly from Linux console. 

See:

[http://linux.dell.com/libsmbios/main/index.html](http://linux.dell.com/libsmbios/main/index.html)

[http://linux.dell.com/libsmbios/main/cmdlinetools.html](http://linux.dell.com/libsmbios/main/cmdlinetools.html)

---

### Post by bimmerd00d on 2007-08-01
Is there a way to adjust teh minimum?  Quickset lets you do it in windows, but that's not an option at this point.

---

### Post by mikeos on 2007-08-09
Currently I don't know the way to do it.  It should be just a matter of some more APIs to be included in the libsmbios package, which does not seem to be actively maintained however. If DELL is seriously willing to support Ubuntu, things will change sooner or later. As usually you can do things yourself by enhancing the libsmbios package following to the Dell documentation (if any) and/or by reverse engineering of the Win32 binaries :)

---

