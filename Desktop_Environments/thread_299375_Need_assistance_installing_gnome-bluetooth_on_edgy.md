---
title: "Need assistance installing gnome-bluetooth on edgy"
date: 2006-11-14
forum: Desktop Environments
---

### Post by zakhooi on 2006-11-14
Hi,

Somehow gnome-bluetooth won't install on Edgy:

```

root@linuxbak:/# apt-get install gnome-bluetooth
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-bluetooth: Depends: libbluetooth1 (>= 2.15) but it is not installable
                   Depends: libbtctl2 (>= 0.5.0) but it is not installable
                   Depends: python2.4-libbtctl but it is not going to be installed
E: Broken packages
root@linuxbak:/# apt-get install libbluetooth1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libbluetooth1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libbluetooth1 has no installation candidate
root@linuxbak:/# apt-get install libbtctl2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libbtctl2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libbtctl2 has no installation candidate
root@linuxbak:/# apt-get install python2.4-libbtctl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.4-libbtctl: Depends: libbtctl2 (>= 0.5.0) but it is not installable
E: Broken packages
root@linuxbak:/# dpkg -l |egrep "libbluetooth1|libbtctl2|python2.4-libbtctl"
rc  libbluetooth1                          2.24-0ubuntu1                         Library to use the BlueZ Linux Bluetooth sta
rc  libbtctl2                              0.6.0-0ubuntu3                        GObject Bluetooth library

```

As you can see the errors are:
E: Package libbluetooth1 has no installation candidate
E: Package libbtctl2 has no installation candidate
E: Broken packages

In case of python2.4-libbtctl it complains that 'depends: libbtctl2 (>= 0.5.0)' but as you can see from the dpkg command it is >= 0.5.0

Synaptic doesn't indicate packages are broken...

Any ideas how to proceed from here?

Thanks in advance

---

### Post by zakhooi on 2006-11-17
bump.....

---

### Post by pavel_kbc on 2006-11-28
get it from here 
[http://packages.ubuntulinux.org/edgy/gnome/gnome-bluetooth](http://packages.ubuntulinux.org/edgy/gnome/gnome-bluetooth)

---

